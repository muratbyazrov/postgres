[Содержание](README.md)

# Optimisation
## Оптимизация запросов

### Индексы

Про индексы подробно на [postgresPro](https://postgrespro.ru/docs/postgresql/11/indexes)

#### Составные индексы:
- Составные индексы по нескольким полям работают и отдельно для этих полей 
- Сущетсвуют частично-составные индексы. Для работы такого индекса необходимо передавать все поля, входящие в индекс. Отдельно работать не будут.
Пример частично-составные индекса: 
```SQL
  "receipts_mt_id_chunk_id_ukey" UNIQUE, btree (transaction_id, chunk_id) WHERE chunk_id IS NOT NULL
  "receipts_mt_id_chunk_null_ukey" UNIQUE, btree (transaction_id) WHERE chunk_id IS NULL
```

### EXPLAIN

EXPLAIN статья на [хабре](https://habr.com/ru/post/203320/), как читать анализ;<br>
EXPLAIN на [PostgresPro](https://postgrespro.ru/docs/postgrespro/14/using-explain), как читать анализ; 


[VACUUM](https://postgrespro.ru/docs/postgrespro/14/sql-vacuum) - провести сборку мусора и, возможно, проанализировать базу данных
VACUUM ANALYZE выполняет очистку (VACUUM), а затем анализ (ANALYZE) всех указанных таблиц. Это удобная комбинация для регулярного обслуживания БД.

[ANALYZE](https://postgrespro.ru/docs/postgrespro/14/sql-analyze) — собрать статистику по базе данных;


Планировщик запроса при работе с индексами работает примерно следующим образом:
- Если количество выдаваемых записей предположительно велико, то проще сканировать каждую страницу последовательно `Seq scan`.
- Если количество выдаваемых записей предположительно не велико, логичнее, что в таком случае лучше использовать индекс (т.е бинарным поиском нужную строку найдем быстрее);
Принудительное использование индексов может быть очень вредно;<br>
[Статья на stackoverflow](https://stackoverflow.com/questions/34537096/postgres-not-using-index-when-index-scan-is-much-better-option)


Каждый индекс увеличивает время INSERT запроса, т.е. индексы нуждаются в обслуживании


---
[Содержание](README.md)
