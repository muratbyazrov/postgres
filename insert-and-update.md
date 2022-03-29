# INSERT and UPDATE
## Вставка и модификация данных


### INSERT 

Документация из [PostgresPro](https://postgrespro.ru/docs/postgrespro/9.5/sql-insert)

За манипуляцию данными в SQL отвечает подмножество DML (Data Manipulation Language), включающее в себя INSERT, UPDATE и DELETE запросы. <br>
SELECT запрос, который не является частью DML, что бы это не значило

Быстрый пример

```SQL
INSERT INTO 
    courses 
        (name, slug, lessons_count, body)
    VALUES 
        ('basics of programming', 'basics', 10, 'this is theory');
```

Вариант выполнения INSERT без перечисления полей. Если они не указаны, то это равносильно их полному перечислению:

```SQL
INSERT INTO 
    courses 
VALUES 
    ('linux', 'linux', 3, 'something about linux');
```

INSERT не является идемпотентным запросом: его повторное выполнение всегда приводит к попытке вставить ещё одну запись, даже если значения остались те же. <br>
Если мы хотим оставить какие-то поля пустыми, то достаточно пропустить их при вставке в обеих частях запроса. <br>
Строки указываются в ординарные кавычки. <br>


### UPDATE

Документация из [PostgresPro](https://postgrespro.ru/docs/postgrespro/9.5/sql-update)

Быстрый пример

```SQL
UPDATE 
    courses
SET 
    body = 'updated!' 
WHERE 
    slug = 'bash';
```


### DELETE

Документация из [PostgresPro](https://postgrespro.ru/docs/postgrespro/9.5/sql-delete)

Быстрый пример

```SQL
DELETE FROM 
    courses 
WHERE 
    slug = 'bash';
```

В базах данных есть ещё один способ удалять данные в таблице — TRUNCATE. Он не является частью стандарта, но реализован большинством баз данных. У него две особенности: <br>

Он предназначен для полной очистки таблиц. <br>
В отличие от DELETE, он выполняется очень эффективно, так как у TRUNCATE нет возможности задавать условия, а значит СУБД не нужно ничего дополнительно анализировать. <br>

```SQL
TRUNCATE courses;
```
