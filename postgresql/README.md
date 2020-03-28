# PostgreSQL Cheat Sheet

### connect 
```sql
psql -U $USERNAME -h $HOST -p $PORT -d $DATABASE
default port : 5432
```
### disconnect
```sql
\q
\!
quit
```
### abort connection or work
```sql
ABORT [WORK | TRANSACTION]
```
### change database owner
```sql
ALTER DATABASE $name OWNER to $new_ownder;
```
### alter user
```sql
ALTER USER name [ [ WITH ] option [ ... ] ]
ALTER USER name RENAME TO new_name
ALTER USER name SET parameter { TO | = } { value | DEFAULT }
ALTER USER name RESET parameter

where option can be :
[ ENCRYPTED | UNENCRYPTED ] PASSWORD 'password'
 | CREATEDB | NOCREATEDB
 | CREATEUSER | NOCREATEUSER
 | VALID UNTIL 'abstime'
```
### create database 
```sql
CREATE DATABASE name
[ [ WITH ] [ OWNER [=] db_owner ]
   [ TEMPLATE [=] template ]
   [ ENCODING [=] encoding ]
   [ TABLESPACE [=] tablespace ] 
]
```
### create user
```
CREATE USER name [ [ WITH ] option [ ... ] ]
Where option can be −

SYSID uid
| [ ENCRYPTED | UNENCRYPTED ] PASSWORD 'password'
| CREATEDB | NOCREATEDB
| CREATEUSER | NOCREATEUSER
| IN GROUP group_name [, ...]
| VALID UNTIL 'abs_time'
```
### list databases
```
\l
```
### list tables
```
\d
```
### connect to database or select database 
```sql
\c $DBNAME
```
and output will be something like this :
```
You are now connected to database "$DBNAME" as user "$USER".
```

### drop database 
```sql
DROP DATABASE [ IF EXISTS ] $name;
```
### insert example 
```sql
INSERT INTO $SCHEMA.$TABLE (column1, column2, column3,...columnN)
VALUES (value1, value2, value3,...valueN);
```


### limit and offset
````sql
select * from COMPANY;
 id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
(7 rows)
````
```sql
 SELECT * FROM COMPANY LIMIT 4;
 id | name  | age | address     | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
(4 rows)
```

```sql
SELECT * FROM COMPANY LIMIT 3 OFFSET 2;
 id | name  | age | address   | salary
----+-------+-----+-----------+--------
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
(3 rows)
```
# create view
```sql
create view user_type_report AS
select upper(user_type) as USER_TYPE, count(user_type) as count
from public.user_account
group by user_type;
```
# grant privilege
```sql
GRANT privilege [, ...]
ON object [, ...]
TO { PUBLIC | GROUP group | username }
```
# revoke privilege
```sql
REVOKE privilege [, ...]
ON object [, ...]
FROM { PUBLIC | GROUP groupname | username }
```
