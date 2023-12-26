### Insert
```sql
sql> INSERT INTO <table_name> (<column1>, <column2>, <column3>, ...) VALUES (<value1>, <value2>, <value3>, ...);
```
### Select
```sql
sql> SELECT * FROM <table_name>;
sql> SELECT <column1>, <column2>... FROM <table_name> WHERE <column1> = 'Lluís' ;
```
### Update
```sql
sql> UPDATE <table_name> SET <column1> = 52 WHERE <column2> = 'Zaragoza';
```
### Delete
```sql
sql> DELETE FROM <table_name> WHERE <column2> = 'Zaragoza';
```
### Commit
Para gravar las transaciones en disco
```sql
sql> COMMIT;
```