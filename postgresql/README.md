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
