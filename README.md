# Итоговая аттестация #

1.Используя команду cat в терминале операционной системы Linux, создать два файла 
Домашние животные(заполнив файл собаками, кошками, хомяками) и 
Вьючные животными заполнив файл Лошадьми, верблюдамии ослы),а затем 
объединить их.
Просмотреть содержимое созданного файла. Переименовать файл,дав ему 
новое имя (Друзья человека). 

2.Создать директорию, переместить файл туда.

![1.jpg](Images/1.jpg)

3.Подключить дополнительный репозиторий MySQL.
Установить любой пакет из этого репозитория. 


![2.png](Images/2.png)

![3.png](Images/3.png)

![3_1.png](Images/3_1.png)

![3_2.png](Images/3_2.png)

4.Установить и удалить deb-пакет с помощью dpkg.

![4.png](Images/4.png)

5.Выложить историю команд в терминале ubuntu

### Task 1 ###
mkdir animals\
cd ~/animals\
cat > home_animals.txt\
cat > pack_animals.txt\
cat home_animals.txt pack_animals.txt > all_animals.txt\
cat all_animals.txt\
mv all_animals human_friends.txt\
ls -l\

### Task 2 ###
cd ..\
mkdir new_animals\
cd ~/new_animals\
mv human_animals.txt new_animals\
cd ~/new_animals\
ls -a\

### Task 3 ###
sudo wget https://dev.mysql.com/get/mysql-apt-config_0.8.23-1_all.deb\
sudo dpkg -i mysql-apt-config_0.8.23-1_all.deb\
sudo apt-get update\
sudo apt-get install mysql-server\

### Task 4 ###
sudo wget https://download.docker.com/linux/ubuntu/dists/jammy/pool/stable/amd64/docker-ce-cli_20.10.13~3-0~ubuntu-jammy_amd64.deb\
sudo dpkg -i docker-ce-cli_20.10.133-0ubuntu-jammy_amd64.deb\
sudo dpkg -r docker-ce-cli\

6.Нарисовать диаграмму,в которой есть класс родительский класс,домашние животные и вьючные животные,в составы 
которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут:
Лошади,верблюды и ослы).

![6.png](Images/6.png)




