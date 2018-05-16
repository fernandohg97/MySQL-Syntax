# MySQL Syntax Documentation

## Basic MySQL Commands


- **SELECT** - extracts data from database

    ```sql
    select column1, column2, ...
    from table_name;
    ```

    or to select all columns

    ```sql
    select * from table_name;
    ```

    - **SELECT DISTINCT** - return only distincts (different values)

        ```sql
        select distinct column1, column2, ...
        from table_name;
        ```
    - **SELECT COUNT** - return the number of rows that matches a specified criteria

        ```sql
        select count(column_name)
        from table_name
        where condition;
        ```

    - **SELECT AVG** - returns the average value of a numeric column

        ```sql
        select avg(column_name)
        from table_name
        where condition;

    - **SELECT SUM** - returns the total sum of a numeric column

        ```sql
        select sum(column_name)
        from table_name
        where condition;

- **UPDATE** -  update data from database

    ```sql
    update table_name
    set column1 = value1, column2 = value2, ...
    where condition;
    ```

- **DELETE** - delete data from database

    ```sql
    delete from table_name
    where condition;
    ```
    **or** delete all rows

    ```sql
    delete from table_name;
    ```

- **INSERT INTO** - inserts new data into table

    ```sql
    insert into table_name (column1, column2, column3, ...)
    values (value1, value2, value3, ...);
    ```

    or add values for all the columns in the table

    ```sql
    insert into table_name
    values (value1, value2, value3, ...);
    ```

- **CREATE DATABASE** - creates a new database

    ```sql
    create database database_name;
    ```

- **ALTER DATABASE** - modifies a database
- **CREATE TABLE** - creates a new table

    ``` sql
    create table table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    ...);
    ```

- **ALTER TABLE** - modifies a table

    - Add column

        ```sql
        alter table table_name
        add column_name datatype;
        ```

    - Drop column

        ```sql
        alter table table_name
        drop column column_name;
        ```

    - Modify column

        ```sql
        alter table table_name
        modify column column_name datatype;
        ```

- **DROP TABLE** - delete a table

    ```sql
    drop table table_name;
    ```

- **CREATE INDEX** - creates an index (search key)

    ```sql
    create INDEX index_name
    on table_name (column1, column2, ...);
    ```

- **DROP INDEX** - delete index

    ```sql
    alter table table_name
    drop index index_name;
    ```

## MySQL Data Types

> `char`, `varchar`, `int`, `smallint`, `numeric`, `float`, `date`, `time`, `timestamp`.


## Operators AND, OR, NOT

- **AND** - displays a record if all the conditions separated by AND is TRUE.

    ```sql
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition1 and condition2 and condition3;
    ```

- **OR** -  displays a record if any of the conditions separated by OR is TRUE.

     ```sql
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition1 or condition2 or condition3;
    ```

- **NOT** - displays a record if the condition(s) is NOT TRUE.

     ```sql
    SELECT column1, column2, ...
    FROM table_name
    WHERE not condition1;
    ```

## MySQL Constraints

- **NOT NULL** - ensures that a column cannot have a null value

    ```sql
    create table table_name (
    column_name1 int not null,
    column_name2 varchar(255) not null,
    column_name3 varchar(255) not null,
    column_name4 int );
    ```

- **UNIQUE** - ensures that all values in a column are different

    ```sql
    create table table_name (
    column_name1 int not null,
    column_name2 varchar(255) not null,
    column_name3 varchar(255) not null,
    column_name4 int,
    unique (column_name1));
    ```

    or alter table

    ```sql
    alter table table_name
    add unique (column_name1);
    ```

- **PRIMARY KEY** - identifier of the table. Not null and unique by default

    ```sql
    create table table_name (
    column_name1 int not null,
    column_name2 varchar(255) not null,
    column_name3 varchar(255) not null,
    column_name4 int,
    primary key (column_name1));
    ```
    
    or alter table

    ```sql
    alter table table_name
    add primary key (column_name1);
    ```

- **FOREIGN KEY** - uniquely identifies a row/record in another table

    ```sql
    create table table_name1 (
    column_name1 int not null,
    column_name2 int not null,
    column_name3 int,
    primary key (column_name1),
    foreign key (column_name3) REFERENCES table_name2(column_name3));
    ```
    
    or alter table

    ```sql
    alter table table_name1
    add foreign key (column_name3) REFERENCES table_name2(column_name3);
    ```

- **CHECK** -  ensures that all values in a column satisfies a specific condition

    ```sql
    create table table_name (
    column_name1 int not null,
    column_name2 varchar(255) not null,
    column_name3 varchar(255),
    column_name4 int,
    check (column_name4 >= 18));
    ```

    or alter table

    ```sql
    alter table table_name
    add check (column_name4 >= 18);
    ```
- **DEFAULT** - sets a default value for a column when no value is specified

    ```sql
    create table table_name (
    column_name1 int not null,
    column_name2 varchar(255) not null,
    column_name3 varchar(255) default 'Francisco',
    column_name4 int
    );
    ```

    or alter table

    ```sql
    alter table table_name
    alter column_name3 set default 'Francisco';
    ```

- **INDEX** - used to create and retrieve data from database quickly

    > Duplicates values are allowed.
    ```sql
    create index index_name
    on table_name (column1, column2, ...);
    ```

    > Duplicates values are not allowed.
    ```sql
    create unique index index_name
    on table_name (column1, column2, ...);
    ```

    or alter table

    ```sql
    alter table table_name
    drop index index_name;
    ```

## MySQL Auto Increment

 ```sql
create table table_name (
column_name1 int not null auto increment,
column_name2 varchar(255) not null,
column_name3 varchar(255),
column_name4 int);
```

To let the AUTO INCREMENT sequence start with another value, use the following SQL statement:

```sql 
alter table table_name auto increment = 100;
```

## MySQL Dates

> MySQL comes with the following data types for storing a date or a date/time value in the database:

- **Date** - format YYYY-MM-DD
- **Datetime** - format: YYYY-MM-DD HH:MI:SS
- **Timestamp** - format: YYYY-MM-DD HH:MI:SS
- **Year** - format YYYY or YY