# SELECT

```SQL
SELECT * FROM users; -- Самый простой пример
```

```SQL
SELECT username, email FROM users; -- Поля необязательно перечислять в том же порядке, в котором они идут в таблице.
```

```SQL
SELECT * FROM users WHERE birthday < '2018-10-21'; --Выборка с условием
```

Выборка с ограничением. В больших таблицах лучше всего пользоваться `LIMIT` 
```SQL
SELECT * FROM users LIMIT 3;
```

В выборках выше не будет никакого порядка. 
Такой запрос отсортирует данные по ключу birthday в прямом порядке: кто родился раньше — будет выше.
```SQL
SELECT * FROM users ORDER BY birthday;
```
Если нужно отсортировать в обратном порядке, то надо добавить ключевое слово DESC (англ. descending — "убывающий").
```SQL
SELECT * FROM users ORDER BY birthday DESC;
```


SELECT может намного больше.
Подробнее на [PostgresPro](https://postgrespro.ru/docs/postgrespro/9.5/sql-select)
