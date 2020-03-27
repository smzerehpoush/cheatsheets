you can use ENUM type for enum values in postgres.
here is an example:
 ```sql
 create type USER_TYPE AS ENUM ('MOBILE_USER','BANK_USER');
```

you can use multidimensional array type in this way.
but unfortunately arrays are 1-based!!!
 ```sql
alter table test."user" add gifts int[];

UPDATE test."user" SET gifts = '{1,2,3}' WHERE id = 1;
select * from test."user" where gifts[1]>0;
```

you can create composite types in this way :
```sql
CREATE TYPE bank_account AS (
    bank_name varchar,
    amount money
);
alter table test."user" add account bank_account;

UPDATE test."user" SET account = ROW('Ayande',10000) WHERE id = 1;

select (account).amount from test."user" where (account).amount >money(10);
```
# CHECK Constraint
The CHECK Constraint enables a condition to check the value being entered into a record.
If the condition evaluates to false, the record violates the constraint and is not entered into the table.
```sql
CREATE TABLE COMPANY5(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL    CHECK(SALARY > 0)
);
```
the union command is to combine the result of two queries without duplicate records.
but union all command includes all rows including duplicate ones. 