# SELECT

```SQL
-- Самый простой пример
SELECT * FROM users; 
```

```SQL
-- Поля необязательно перечислять в том же порядке, в котором они идут в таблице.
SELECT username, email FROM users;
```

```SQL
--Выборка с условием
SELECT * FROM users WHERE birthday < '2018-10-21';
```

```SQL
-- Выборка с ограничением. В больших таблицах лучше всегда использовать `LIMIT`, чтобы случайно не сильно не нагрузить БД
SELECT * FROM users LIMIT 3;
```

```SQL
-- Такой запрос отсортирует данные по ключу birthday в прямом порядке: кто родился раньше — будет выше.
SELECT * FROM users ORDER BY birthday;
```

```SQL
-- Если нужно отсортировать в обратном порядке, то надо добавить ключевое слово DESC (англ. descending — "убывающий").
SELECT * FROM users ORDER BY birthday DESC;
```


SELECT может намного больше.
Подробнее на [PostgresPro](https://postgrespro.ru/docs/postgrespro/9.5/sql-select)
