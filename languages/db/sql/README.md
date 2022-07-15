---
description: Structured Query Language
---

# 📑 SQL

sqlMaterials:

[https://tproger.ru/translations/sql-recap/](https://tproger.ru/translations/sql-recap/) - прочитать\
[https://postgrespro.ru/docs/postgresql/12/index](https://postgrespro.ru/docs/postgresql/12/index) - документация

Курс - [https://geekbrains.ru/chapters/1157](https://geekbrains.ru/chapters/1157)

## Basic:

СУБД - система управления базами данных

### Правила проектирования:

Атомарная структура (ячейка содержит только одно значение, не несколько)

Правило №1: Все элементы внутри ячеек должны быть атомарными.\
Правило №2 Все строки должны быть различными.\
Правило №3 Любое поле таблицы, не входящее в состав первичного ключа, функционально полно зависит от первичного ключа.\
Правило №4 Все предыдущие правила, и плюс то, что любой функциональный атрибут зависит только от первичного ключа.

## Синтаксис

### Команды для работы с базами данных

#### 1. Просмотр доступных баз данных

```sql
SHOW DATABASES;
```

#### 2. Создание новой базы данных

```sql
CREATE DATABASE;
```

#### 3. Выбор базы данных для использования

```sql
USE <database_name>; 
```

#### 4. Импорт SQL-команд из файла .sql

```sql
SOURCE <path_of_.sql_file>; 
```

#### 5. Удаление базы данных

```sql
DROP DATABASE <database_name>; 
```

### Работа с таблицами

#### 6. Просмотр таблиц, доступных в базе данных

```sql
SHOW TABLES; 
```

#### 7. Создание новой таблицы

```sql
CREATE TABLE <table_name1> (
  <col_name1> <col_type1>,
  <col_name2> <col_type2>,
  <col_name3> <col_type3>
  PRIMARY KEY (<col_name1>),
  FOREIGN KEY (<col_name2>) REFERENCES <table_name2>(<col_name2>)
); 
```

**Ограничения целостности при использовании CREATE TABLE**

Может понадобиться создать ограничения для определённых столбцов в таблице. При создании таблицы можно задать следующие ограничения:

* ячейка таблицы не может иметь значение NULL;
* первичный ключ — `PRIMARY KEY (col_name1, col_name2, …)`;
* внешний ключ — `FOREIGN KEY (col_namex1, …, col_namexn) REFERENCES table_name(col_namex1, …, col_namexn)`.

Можно задать больше одного первичного ключа. В этом случае получится составной первичный ключ.

#### 8. Сведения о таблице

Можно просмотреть различные сведения (тип значений, является ключом или нет) о столбцах таблицы следующей командой:

```
DESCRIBE <table_name>; 
```

#### 9. Добавление данных в таблицу

```
INSERT INTO <table_name> (<col_name1>, <col_name2>, <col_name3>, …)
  VALUES (<value1>, <value2>, <value3>, …); 
```

При добавлении данных в каждый столбец таблицы не требуется указывать названия столбцов.

```
INSERT INTO <table_name>
  VALUES (<value1>, <value2>, <value3>, …); 
```

#### 10. Обновление данных таблицы

```
UPDATE <table_name>
  SET <col_name1> = <value1>, <col_name2> = <value2>, ...
  WHERE <condition>; 
```

#### 11. Удаление всех данных из таблицы

```
DELETE FROM <table_name>; 
```

#### 12. Удаление таблицы

```
DROP TABLE <table_name>; 
```

### Команды для создания запросов

#### 13. SELECT

`SELECT` используется для получения данных из определённой таблицы:

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>; 
```

Следующей командой можно вывести все данные из таблицы:

```
SELECT * FROM <table_name>; 
```

#### 14. SELECT DISTINCT

В столбцах таблицы могут содержаться повторяющиеся данные. Используйте `SELECT DISTINCT` для получения только неповторяющихся данных.

```
SELECT DISTINCT <col_name1>, <col_name2>, …
  FROM <table_name>; 
```

#### 15. WHERE

Можно использовать ключевое слово `WHERE` в `SELECT` для указания условий в запросе:

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  WHERE <condition>; 
```

В запросе можно задавать следующие условия:

* сравнение текста;
* сравнение численных значений;
* логические операции AND (и), OR (или) и NOT (отрицание)

#### 16. GROUP BY

Оператор `GROUP BY` часто используется с агрегатными функциями, такими как `COUNT`, `MAX`, `MIN`, `SUM` и `AVG`, для группировки выходных значений.

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  GROUP BY <col_namex>; 
```

#### 17. HAVING

Ключевое слово `HAVING` было добавлено в SQL потому, что `WHERE` не может быть использовано для работы с агрегатными функциями.

```
SELECT <col_name1>, <col_name2>, ...
  FROM <table_name>
  GROUP BY <column_namex>
  HAVING <condition> 
```

#### 18. ORDER BY

`ORDER BY` используется для сортировки результатов запроса по убыванию или возрастанию. `ORDER BY` отсортирует по возрастанию, если не будет указан способ сортировки `ASC` или `DESC`.

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  ORDER BY <col_name1>, <col_name2>, … ASC|DESC; 
```

#### 19. BETWEEN

`BETWEEN` используется для выбора значений данных из определённого промежутка. Могут быть использованы числовые и текстовые значения, а также даты.

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  WHERE <col_namex> BETWEEN <value1> AND <value2>; 
```

#### 20. LIKE

Оператор `LIKE` используется в `WHERE`, чтобы задать шаблон поиска похожего значения.\
Есть два свободных оператора, которые используются в `LIKE`:

* `%` (ни одного, один или несколько символов);
* `_` (один символ).

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  WHERE <col_namex> LIKE <pattern>; 
```

#### 21. IN

С помощью `IN` можно указать несколько значений для оператора `WHERE`:

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  WHERE <col_namen> IN (<value1>, <value2>, …); 
```

#### 22. JOIN

`JOIN` используется для связи двух или более таблиц с помощью общих атрибутов внутри них. На изображении ниже показаны различные способы объединения в SQL. Обратите внимание на разницу между левым внешним объединением и правым внешним объединением:

![](<../../../.gitbook/assets/image (9).png>)

```
SELECT <col_name1>, <col_name2>, …
  FROM <table_name1>
  JOIN <table_name2>
  ON <table_name1.col_namex> = <table2.col_namex>; 
```

#### 23. View

`View` — это виртуальная таблица SQL, созданная в результате выполнения выражения. Она содержит строки и столбцы и очень похожа на обычную SQL-таблицу. `View` всегда показывает самую свежую информацию из базы данных.

**Создание**

```
CREATE VIEW <view_name> AS
  SELECT <col_name1>, <col_name2>, …
  FROM <table_name>
  WHERE <condition>; 
```

**Удаление**

```
DROP VIEW <view_name>; 
```

#### 24. Агрегатные функции

Эти функции используются для получения совокупного результата, относящегося к рассматриваемым данным. Ниже приведены общеупотребительные агрегированные функции:

* `COUNT (col_name)` — возвращает количество строк;
* `SUM (col_name)` — возвращает сумму значений в данном столбце;
* `AVG (col_name)` — возвращает среднее значение данного столбца;
* `MIN (col_name)` — возвращает наименьшее значение данного столбца;
* `MAX (col_name)` — возвращает наибольшее значение данного столбца.

#### 25. Вложенные подзапросы

Вложенные подзапросы — это SQL-запросы, которые включают выражения `SELECT`, `FROM` и `WHERE`, вложенные в другой запрос.