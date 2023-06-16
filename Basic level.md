# Содержание
1. [Создание базы данных](https://github.com/Analyst-Vadim/SQL-Examples/blob/main/Basic%20level.md#создание-базы-данных)
2. [Изменение схемы](https://github.com/Analyst-Vadim/SQL-Examples/blob/main/Basic%20level.md#изменение-схемы-данных)

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

После создания таблицы нужно добавить в неё данные. Делается это с помощью ключевых слов _INSERT INTO_, после которых указывается название таблицы и в скобках поля, в которые мы будем добавлять данные и _VALUES_, где мы указываем сами данные.

>INSERT INTO Managers (Manager_Name, Manager_LastName, Manager_Mail) \
>VALUES \
>('Vasiliy', 'Petrov', 'vasya@mail.ru'), \
>('Ivan', 'Nicolarv', 'Ivan@gmail.com'), \
>('Cate', 'Manulaeva', 'Catalis@bk.ru'), \
>('Dan', 'Chikunov' 'DenIs@mail.ru');

В итоге получим следующую таблицу

![image](https://github.com/Analyst-Vadim/SQL-Examples/assets/85847435/b99aef5a-e869-41eb-8d7c-78aa1a481bef)

После создания всех таблиц, можно посмотреть их в нашей базе с помощью команды _\dt_

![image](https://github.com/Analyst-Vadim/SQL-Examples/assets/85847435/09934ee9-324c-4ea0-8549-d829e8051c41)

Также получить название всех таблиц можно с помощью команды 
> select * from information_schema.tables

# Изменение схемы данных
