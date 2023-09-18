# Итоговая аттестация #

**1.Используя команду cat в терминале операционной системы Linux, создать два файла 
Домашние животные(заполнив файл собаками, кошками, хомяками) и 
Вьючные животными заполнив файл Лошадьми, верблюдамии ослы),а затем 
объединить их.
Просмотреть содержимое созданного файла. Переименовать файл,дав ему 
новое имя (Друзья человека).** 

**2.Создать директорию, переместить файл туда.**

![1.jpg](Images/1.jpg)

**3.Подключить дополнительный репозиторий MySQL.
Установить любой пакет из этого репозитория.** 


![2.png](Images/2.png)

![3.png](Images/3.png)

![3_1.png](Images/3_1.png)

![3_2.png](Images/3_2.png)

**4.Установить и удалить deb-пакет с помощью dpkg.**

![4.png](Images/4.png)

**5.Выложить историю команд в терминале ubuntu**

#### Task 1 ####
mkdir animals\
cd ~/animals\
cat > home_animals.txt\
cat > pack_animals.txt\
cat home_animals.txt pack_animals.txt > all_animals.txt\
cat all_animals.txt\
mv all_animals human_friends.txt\
ls -l\

#### Task 2 ####
cd ..\
mkdir new_animals\
cd ~/new_animals\
mv human_animals.txt new_animals\
cd ~/new_animals\
ls -a\

#### Task 3 ####
sudo wget https://dev.mysql.com/get/mysql-apt-config_0.8.23-1_all.deb\
sudo dpkg -i mysql-apt-config_0.8.23-1_all.deb\
sudo apt-get update\
sudo apt-get install mysql-server\

#### Task 4 ####
sudo wget https://download.docker.com/linux/ubuntu/dists/jammy/pool/stable/amd64/docker-ce-cli_20.10.13~3-0~ubuntu-jammy_amd64.deb\
sudo dpkg -i docker-ce-cli_20.10.133-0ubuntu-jammy_amd64.deb\
sudo dpkg -r docker-ce-cli\

**6.Нарисовать диаграмму,в которой есть класс родительский класс,домашние животные и вьючные животные,в составы 
которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут:
Лошади,верблюды и ослы).**

![6.png](Images/6.png)

**7.В подключенном MySQL репозитории создать базу данных “Друзья
   человека”**

CREATE DATABASE Human_friends;

**8.Создать таблицы с иерархией из диаграммы в БД**

USE Human_friends;\
CREATE TABLE animal_classes\
(\
Id INT AUTO_INCREMENT PRIMARY KEY,\
Class_name VARCHAR(20)\
);

INSERT INTO animal_classes (Class_name)\
VALUES ('вьючные'),\
('домашние');


CREATE TABLE packed_animals\
(\
Id INT AUTO_INCREMENT PRIMARY KEY,\
Genus_name VARCHAR (20),\
Class_id INT,\
FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);

INSERT INTO packed_animals (Genus_name, Class_id)\
VALUES ('Лошади', 1),\
('Ослы', 1),  \
('Верблюды', 1);

CREATE TABLE home_animals\
(\
Id INT AUTO_INCREMENT PRIMARY KEY,\
Genus_name VARCHAR (20),\
Class_id INT,\
FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);

INSERT INTO home_animals (Genus_name, Class_id)\
VALUES ('Кошки', 2),\
('Собаки', 2),  \
('Хомяки', 2);

CREATE TABLE cats\
(       \
Id INT AUTO_INCREMENT PRIMARY KEY,\
Name VARCHAR(20),\
Birthday DATE,\
Commands VARCHAR(50),\
Genus_id int,\
Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);

**9.Заполнить низкоуровневые таблицы именами(животных), командами
которые они выполняют и датами рождения**

INSERT INTO cats (Name, Birthday, Commands, Genus_id)\
VALUES ('Мурзик', '2021-01-01', 'кс-кс-кс', 1),\
('Васька', '2022-01-01', "фу!", 1), \ 
('Ваучер', '2023-01-01', "", 1);

CREATE TABLE dogs\
(       
Id INT AUTO_INCREMENT PRIMARY KEY,\
Name VARCHAR(20),\
Birthday DATE,\
Commands VARCHAR(50),\
Genus_id int,\
Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);\
INSERT INTO dogs (Name, Birthday, Commands, Genus_id)\
VALUES ('Шарик', '2020-01-01', 'ко мне, голос', 2),\
('Тузик', '2022-06-12', "сидеть, лапу", 2),  \
('Плуто', '2018-02-01', "сидеть,  фас", 2),\
('Чубайс', '2016-03-10', "сидеть,  место", 2);

CREATE TABLE hamsters
(       
Id INT AUTO_INCREMENT PRIMARY KEY,\
Name VARCHAR(20),\
Birthday DATE,\
Commands VARCHAR(50),\
Genus_id int,\
Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);
INSERT INTO hamsters (Name, Birthday, Commands, Genus_id)\
VALUES ('Хомяк1', '2023-12-11', NULL, 3),\
('Хомяк2', '2023-01-11', NULL, 3),\  
('Хомяк3', '2023-03-10', NULL, 3),\
('Хомяк4', '2023-05-10', NULL, 3);

CREATE TABLE horses
(       
Id INT AUTO_INCREMENT PRIMARY KEY,\
Name VARCHAR(20),\
Birthday DATE,\
Commands VARCHAR(50),\
Genus_id int,\
Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);
INSERT INTO horses (Name, Birthday, Commands, Genus_id)\
VALUES ('Лошадь1', '2015-01-12', NULL, 1),\
('Лошадь', '2017-03-12', "рысью", 1),\
('Лошадь3', '2016-07-12', "бегом ", 1),\
('Лошадь4', '2028-11-10', "шагом", 1);

CREATE TABLE donkeys
(       
Id INT AUTO_INCREMENT PRIMARY KEY,\
Name VARCHAR(20),\
Birthday DATE,\
Commands VARCHAR(50),\
Genus_id int,\
Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE\
);
INSERT INTO donkeys (Name, Birthday, Commands, Genus_id)\
VALUES ('Осел1', '2020-05-10', NULL, 2),\
('Осел2', '2019-06-12', "", 2), \
('Осел3', '2017-08-12', "", 2),\
('Осел4', '2018-10-10', NULL, 2);\

CREATE TABLE camels
(       
Id INT AUTO_INCREMENT PRIMARY KEY,\
Name VARCHAR(20),\
Birthday DATE,\
Commands VARCHAR(50),\
Genus_id int,\
Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO camels (Name, Birthday, Commands, Genus_id)\
VALUES ('Верблюд1', '2022-04-10', NULL, 3),\
('Верблюд2', '2019-03-12', NULL, 3), \ 
('Верблюд3', '2015-07-12', NULL, 3),\
('Верблюд4', '2022-12-10', NULL, 3);



