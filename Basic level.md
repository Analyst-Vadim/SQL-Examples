# Содержание
1. [Создание базы данных](https://github.com/Analyst-Vadim/SQL-Examples/blob/main/Basic%20level.md#создание-базы-данных)
2. [Изменение схемы](https://github.com/Analyst-Vadim/SQL-Examples/blob/main/Basic%20level.md#изменение-схемы-данных)
3. [Запросы](https://github.com/Analyst-Vadim/SQL-Examples/edit/main/Basic%20level.md#запросы)

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
>('Dan', 'Chikunov' 'DenIs');

В итоге получим следующую таблицу

![image](https://github.com/Analyst-Vadim/SQL-Examples/assets/85847435/9dd44d5f-bf56-4c5e-ab91-10762a22c968)

После создания всех таблиц, можно посмотреть их в нашей базе с помощью команды _\dt_

![image](https://github.com/Analyst-Vadim/SQL-Examples/assets/85847435/09934ee9-324c-4ea0-8549-d829e8051c41)

Также получить название всех таблиц можно с помощью команды 
> SELECT * FROM information_schema.tables

# Изменение схемы данных

В процессе работы с базой данных может возникнуть потребность не только в написании запросов, но и изменение как самих таблиц, так и данных внутри них.
Например в процессе работы мы поняли, что название столбца не является уникальным и путает. Поэтому надо его изменить.
Для этого используется ключевое слово _ALTER TABLE_. Данная команда позволяет изменить саму таблицу.
> ALTER TABLE managers RENAME COLUMN Manager_Name TO Maneger_FirstName;

Или нужно изменить значение. В нашем примере у менеджера Дениса некорректный адрес электронной почты.
Обновляются значения с помощью команды _UPDATE_
> UPDATE TABLE managers SET Manager_Mail = 'Denis@mail.ru' WHERE Manager_ID = 4

Можно обновлять несколько полей сразу, можно задавать несколько условий.

# Запросы
Основная работа аналитика с SQL заключается в написании запросов к базе данных. Запросы бывают разной сложности, начиная от простого вывода какого-то поля или поиска максимального значения, и заканчивая подзапросами, оконными функциями и CTE. 
Но на самом деле всё это не так сложно и мы всё понемногу разберём.

Самый простой тип запроса - вывести конкретные поля / все:
> SELECT Manager_FirstName FROM Managers;
> SELECT * FROM Managers;

![image](https://github.com/Analyst-Vadim/SQL-Examples/assets/85847435/598ed8e7-83cc-41c7-affa-f4350e1cedde)
![image](https://github.com/Analyst-Vadim/SQL-Examples/assets/85847435/dacea658-844b-4ef9-8344-f50fdc8a66d3)
