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

  
