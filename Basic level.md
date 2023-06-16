# Создание базы данных 
Создадим базу данных с названием mydb:
> CREATE DATABASE IF NOT EXISTS mydb;

Условие "IF NOT EXISTS" проверяет наличиие создаваемой базы в уже имющийхся.
Перейдём в созданную базу данных:
> USE mydb;

Мы можем посмотреть имеющиеся таблицы, но там будет пусто. Поэтому начнём создавать таблицы.
Разберём в качестве примера таблицу Managers, остальные создаются аналогичным образом.
>CREATE TABLE Managers (
              Manager_ID SMALLINT AUTO_INCREMENT PRIMARY KEY, \
              Manager_Name VARCHAR(50), \
              Manager_LastName VARCHAR(50), \
              Manager_Mail VARCHAR(70) NOT NULL, \
              CONSTRAINT unique_email UNIQUE(Manager_Mail)\
                        );
