# 12-02_ddl_dml
HW_12-02_DDL/DML

# Домашнее задание к занятию 2 «Работа с данными (DDL/DML)»

### Задание 1.
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker:

Установим **MySQL** на виртуальной машине **Debian 11.6**, которая будет использоваться в качестве локального
сервера.

- Добавим **MySQL APT-репозиторий** в системный список репозиториев, предварительно скачав **mysql-apt-config_0.8.26-1_all.deb**
  с официального сайта [MySQL Community Downloads](https://dev.mysql.com/downloads/file/?id=521319) :
```
sudo dpkg -i ./mysql_apt-config/mysql-apt-config_0.8.26-1_all.deb
```
<kbd>![](img/mysql_apt_config_installation.png)</kbd>  

- Обновление **APT-кэша**:
```
sudo apt update
```
<kbd>![](img/mysql_apt_repos_update.png)</kbd>
- Установка **MySQL** с помощью **APT**:
```
sudo apt install mysql-server
```
- Зададим пароль для рута:
  
<kbd>![](img/mysql_server_installation_root_password.png)</kbd>

- После инсталляции **MySQL** проверим версию установленного продукта:
```
mysql -V
```
<kbd>![](img/mysql_version.png)</kbd>

- Проверим статус работы сервиса **mysql.service**:
```
systemctl status mysql.service
```
<kbd>![](img/mysql_service_status.png)</kbd>

1.2. Создайте учётную запись sys_temp.
- Зайдем в консоль **MySQL** под пользователем **root**:
```
sudo mysql -u root -p
```
<kbd>![](img/mysql_console_root.png)</kbd>

- Создадим пользователя **sys_temp** c паролем **12345**:
```
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY '12345';
```
<kbd>![](img/create_user_sys_temp.png)</kbd>

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот):
```
SELECT user FROM mysql.user;
```
<kbd>![](img/select_user.png)</kbd>

1.4. Дайте все права для пользователя sys_temp:
```
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';
```
<kbd>![](img/sys_temp_grant_all_privileges.png)</kbd>

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот):
```
SHOW GRANTS FOR 'sys_temp'@'localhost';
```
<kbd>![](img/show_grants_sys_temp.png)</kbd>

1.6. Переподключитесь к базе данных от имени sys_temp:
```
sudo mysql -u systemp -p
```
<kbd>![](img/sys_temp_db_log_in.png)</kbd>

- Создадим новую базу данных **dvdrental**:
```
CREATE DATABASE dvd_rental;
```
<kbd>![](img/create_db_dvd_rental.png)</kbd>

- Проверим список баз данных в системе:
```
SHOW DATABASES;
```
<kbd>![](img/show_databases_dvd_rental.png)</kbd>

- По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных и распакуем архив
  **sakila-db.zip** в директорию **/home/mityaevg/sakila-db**:
```
https://downloads.mysql.com/docs/sakila-db.zip
unzip sakila-db.zip
ls -l ./sakila-db
```
<kbd>![](img/ls-l_sakila-db.png)</kbd>

1.7. Восстановите дамп в базу данных:

- Сначала скачаем и установим программу **DBeaver**:
```
wget https://dbeaver.io/files/dbeaver-ce_latest_amd64.deb
sudo dpkg -i  dbeaver-ce_latest_amd64.deb
dbeaver &
```
- Восстановим дамп в базу **dvd_rental**:

<kbd>![](img/dbeaver_restore_database.png)</kbd>
```
/usr/bin
```

- Сначала импортируем **/home/mityaevg/sakila-db/sakila-schema.sql**:

<kbd>![](img/restore_sakila-schema_sql.png)</kbd>

- Затем импортируем **/home/mityaevg/sakila-db/sakila-data.sql**:

<kbd>![](img/restore_sakila-data_sql.png)</kbd>

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных:

<kbd>![](img/sakila-database_entity_relationship_diagram.png)</kbd>

### Задание 2.
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст).

![image](https://github.com/mityaevg/12-02_ddl_dml/assets/121676200/2dd07525-1fe0-480e-bac8-45a54f04c2dc)

