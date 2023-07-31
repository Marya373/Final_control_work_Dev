<details>
<summary>Задание проекта</summary>1. Используя команду cat в терминале операционной системы Linux, создать два файла Домашние животные (заполнив файл собаками, кошками, хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и ослы), а затем объединить их. Просмотреть содержимое созданного файла. Переименовать файл, дав ему новое имя (Друзья человека). 2. Создать директорию, переместить файл туда. 3. Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория. 4. Установить и удалить deb-пакет с помощью dpkg. 5. Выложить историю команд в терминале ubuntu 6. Нарисовать диаграмму, в которой есть класс родительский класс, домашние животные и вьючные животные, в составы которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут: Лошади, верблюды и ослы). 7. В подключенном MySQL репозитории создать базу данных “Друзья человека” 8. Создать таблицы с иерархией из диаграммы в БД 9. Заполнить низкоуровневые таблицы именами(животных), командами которые они выполняют и датами рождения 10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу. 11.Создать новую таблицу “молодые животные” в которую попадут все животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью до месяца подсчитать возраст животных в новой таблице 12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на прошлую принадлежность к старым таблицам. 13.Создать класс с Инкапсуляцией методов и наследованием по диаграмме. 14. Написать программу, имитирующую работу реестра домашних животных. В программе должен быть реализован следующий функционал: 14.1 Завести новое животное 14.2 определять животное в правильный класс 14.3 увидеть список команд, которое выполняет животное 14.4 обучить животное новым командам 14.5 Реализовать навигацию по меню 15.Создайте класс Счетчик, у которого есть метод add(), увеличивающий̆ значение внутренней̆int переменной̆на 1 при нажатие “Завести новое животное” Сделайте так, чтобы с объектом такого типа можно было работать в блоке try-with-resources. Нужно бросить исключение, если работа с объектом типа счетчик была не в ресурсном try и/или ресурс остался открыт. Значение считать в ресурсе try, если при заведения животного заполнены все поля.</details>

Решение выполняется в Ubuntu


<details>
<summary>Команды Bash (развернуть)</summary>
cat > "Домашние животные"
Собаки
Кошки
Хомяки

'Ctrl+d'

cat > "Вьючные животные"
Лошади
Верблюды
Ослы

'Ctrl+d'

cat "Домашние животные" "Вьючные животные" > Animals

cat Animals

mv "Animals" "Друзья человека"

mkdir folder_for_attestation

mv 'Друзья человека' folder_for_attestation/

ls
cd folder_for_attestation/

ls

sudo apt-get update

sudo apt update

sudo apt install mysql-server

sudo service mysql status

wget http://ftp.us.debian.org/debian/pool/main/s/sl/sl_5.02-1_amd64.deb

sudo dpkg -i sl_5.02-1_amd64.deb

wget http://archive.ubuntu.com/ubuntu/pool/universe/s/sl/sl_5.02-1_amd64.deb

sudo dpkg -r sl

mkdir attestation

cd attestation/

cat > Домашние животные

cat > "Домашние животные"

cat > "Вьючные животные"

cat "Домашние животные" "Вьючные животные" > Animals 

cat Animals

mv "Animals" "Друзья человека"

clear

mkdir "Друзья человека"

mkdir folder_for_attestation && mv "Друзья человека" /attestation/folder_for_attestation 

ls

mv "Друзья человека" /attestation/folder_for_attestation

mv "Друзья человека" attestation/folder_for_attestation

mkdir folder_for_attestation

mv 'Друзья человека' attestation/folder_for_attestation/

mv 'Друзья человека' folder_for_attestation/</details>

mysql -u marya373 -p

CREATE DATABASE Друзья_человека;

<details>
<summary>SQL запросы (развернуть)</summary>

CREATE TABLE Родительский_класс (
  id INT PRIMARY KEY AUTO_INCREMENT,
  тип VARCHAR(50)
);

CREATE TABLE Домашние_животные (
  id INT PRIMARY KEY,
  вид VARCHAR(50),
  FOREIGN KEY (id) REFERENCES Родительский_класс(id)
);

CREATE TABLE Собаки (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Домашние_животные(id)
);

CREATE TABLE Кошки (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Домашние_животные(id)
);

CREATE TABLE Хомяки (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Домашние_животные(id)
);

CREATE TABLE Вьючные_животные (
  id INT PRIMARY KEY,
  вид VARCHAR(50),
  FOREIGN KEY (id) REFERENCES Родительский_класс(id)
);

CREATE TABLE Лошади (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Вьючные_животные(id)
);

CREATE TABLE Верблюды (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Вьючные_животные(id)
);

CREATE TABLE Ослы (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Вьючные_животные(id)
);</details>

show databases;
show tables;

<details>
<summary>SQL запросы (развернуть)</summary>

INSERT INTO Верблюды ( имя, команда, дата_рождения)
VALUES ('Руль', 'пошел', '2020-09-01'),
       ('Педаль', 'на месте' '2020-10-12'),
       ('Горб', 'смирно' '2020-05-06');

INSERT INTO Кошки ( имя, команда, дата_рождения)
VALUES ('Лютик', 'мяу', '2007-01-01'),
       ('Мурзик', 'играй', '2005-01-01');

INSERT INTO Лошади ( имя, команда, дата_рождения)
VALUES ('Пони', 'нуууу', '2007-02-01'),
       ('Птица', 'пруууу', '2007-03-01');

INSERT INTO Ослы ( имя, команда, дата_рождения)
VALUES ('Конь', 'иди', '2020-08-06'),
       ('Осел', 'стой', '2020-09-06');

INSERT INTO Собаки ( имя, команда, дата_рождения)
VALUES ('Маня', 'лапу', '2019-07-25'),
       ('Бобик', 'хвост', '2019-05-09');

INSERT INTO Хомяки ( имя, команда, дата_рождения)
VALUES ('Пушистик', 'лежи', '2007-01-20'),
       ('Лысый', 'сиди', '2022-05-05');</details>

<details>
<summary>SQL запросы (развернуть)</summary>
TRUNCATE TABLE Верблюды;
CREATE TABLE Парнокопытные AS
SELECT * FROM Лошади
UNION
SELECT * FROM Ослы;</details>


<details>
<summary>SQL запросы (развернуть)</summary>
CREATE TABLE Парнокопытные AS
SELECT *, TIMESTAMPDIFF(MONTH, дата_рождения, CURDATE()) AS возраст_в_месяцах
FROM (
    SELECT 'Собаки' AS тип_животного, имя, команда, дата_рождения FROM Собаки
    UNION ALL
    SELECT 'Кошки' AS тип_животного, имя, команда, дата_рождения FROM Кошки
    UNION ALL
    SELECT 'Хомяки' AS тип_животного, имя, команда, дата_рождения FROM Хомяки
    UNION ALL
    SELECT 'Лошади' AS тип_животного, имя, команда, дата_рождения FROM Лошади
    UNION ALL
    SELECT 'Ослы' AS тип_животного, имя, команда, дата_рождения FROM Ослы
) AS животные
WHERE дата_рождения >= DATE_SUB(CURDATE(), INTERVAL 3 YEAR)
AND дата_рождения <= DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
</details>

<details>
<summary>SQL запросы (развернуть)</summary>
CREATE TABLE Полный_состав AS
SELECT 'Собаки' AS тип_животного, имя, команда, дата_рождения FROM Собаки
UNION ALL
SELECT 'Кошки' AS тип_животного, имя, команда, дата_рождения FROM Кошки
UNION ALL
SELECT 'Хомяки' AS тип_животного, имя, команда, дата_рождения FROM Хомяки
UNION ALL
SELECT 'Лошади' AS тип_животного, имя, команда, дата_рождения FROM Лошади
UNION ALL
SELECT 'Ослы' AS тип_животного, имя, команда, дата_рождения FROM Ослы;</details>
