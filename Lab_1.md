ЛР №1
Проектування БД, універсальне відношення, створення таблиць (головний ключ, обмеження), створення індексі і завантаження даних
Усі завдання цієї та наступних лабораторних виконуються в СУБД, що підтримує SQL.
1. Проаналізувати приклад універсального відношення. Вирішити яка його колонка буде головним ключем, які поля обов'язкові для введення, які
поля мають значення за замовчуванням, які поля мають область допустимих значень, які поля необхідно проіндексувати.
2. Скласти SQL-script, який виконує:
a. Видалення попередньої версії бази даних
DROP DATABASE firstlab;
b. Створення бази даних
CREATE DATABASE firstlab;
c. Створення таблиці на основі універсального відношення. Команда для створення таблиці повинна містити головний ключ, обмеження
типу null / not null, default, check. ЗВЕРНІТЬ УВАГУ!!! Усі поля повинні мати назви латиницею!
CREATE TABLE book (
n int (200) NOT NULL UNIQUE AUTO_INCREMENT,
title VARCHAR(100) NOT NULL,
price float(30) NOT NULL,
date date NOT NULL DEFAULT '2021-11-11',
PRIMARY KEY (n));
d. Створення додаткового індексу.
ALTER TABLE book
ADD code varchar(30) NOT NULL DEFAULT '00';
e. Завантаження даних в таблицю
INSERT INTO book (title, price, date, code)
VALUES('Апаратні засоби мультимедіа. Відеосистема
РС',22.50,' 2011-10-5','022'), 
('Засвой самостійно модернізацію та ремонт
ПК за 24 години, 2-ге вид.',18.90,'07/07/2000','4985'),
('Структури даних та алгоритми',37.80,'9/29/2000','5141');
3. Скласти SQL-script, який виконує:
a. Додавання в таблицю нового текстового поля "Автор", розміром 15 символів
ALTER TABLE book
ADD author varchar(15) NOT NULL DEFAULT 'announ';
b. Збільшення розміру текстового поля "Автор" до 20 символів
ALTER TABLE book
MODIFY COLUMN author varchar(20);
c. Видалення текстового поля "Автор" з таблиці
ALTER TABLE book
DROP COLUMN author;
e. Видалення індексу
ALTER TABLE book
DROP COLUMN n;


КОД
CREATE TABLE book (
n int (200) NOT NULL UNIQUE AUTO_INCREMENT,
title VARCHAR(100) NOT NULL,
price float(30) NOT NULL,
date date NOT NULL DEFAULT '2021-11-11',
PRIMARY KEY (n));

ALTER TABLE book
ADD code varchar(30) NOT NULL DEFAULT '00';

INSERT INTO book (title, price, date, code)
VALUES('Апаратні засоби мультимедіа. Відеосистема
РС',22.50,' 2011-10-5','022'), 
('Засвой самостійно модернізацію та ремонт
ПК за 24 години, 2-ге вид.',18.90,'07/07/2000','4985'),
('Структури даних та алгоритми',37.80,'9/29/2000','5141');

ALTER TABLE book
ADD author varchar(15) NOT NULL DEFAULT 'announ';
ALTER TABLE book
MODIFY COLUMN author varchar(20);
ALTER TABLE book
DROP COLUMN author;
ALTER TABLE book
DROP COLUMN n;
