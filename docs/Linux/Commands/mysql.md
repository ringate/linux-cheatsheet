mysql & mysqldump
=================

Export/Import SQL File
----------------------

##### Export database as SQL file
```
$ mysqldump -p -u dbuser databasename > project_YYYYMMDD.sql
Enter password:
```

##### Export database as SQL file with gzip
```
$ mysqldump -p -u dbuser databasename | gzip > project_YYYYMMDD.sql.gz
Enter password:
```

##### Export all databases with gzip
```
$ mysqldump -u dbuser -p --all-databases | gzip > all-dbs_YYYYMMDD.sql.gz
Enter password:
```

##### Import SQL file to specific database
```
$ mysql -p -u dbuser databasename < project_YYYYMMDD.sql
Enter password:
```

##### Import gzipped SQL file to specific database
```
$ gunzip < project_YYYYMMDD.sql.gz | mysql -p -u dbuser databasename
Enter password:
```


Drop All Tables
---------------

By SQL statements
```
SET FOREIGN_KEY_CHECKS = 0;
SET @tables = NULL;
SELECT GROUP_CONCAT(table_schema, '.', table_name) INTO @tables
  FROM information_schema.tables
  WHERE table_schema = 'database_name'; -- specify DB name here.

SET @tables = CONCAT('DROP TABLE ', @tables);
PREPARE stmt FROM @tables;
EXECUTE stmt;
DEALLOCATE PREPARE stmt;
SET FOREIGN_KEY_CHECKS = 1;
```

##### Reference Link
* http://stackoverflow.com/questions/12403662/how-to-remove-all-mysql-tables-from-the-command-line-without-drop-database-permi


mysqldump Options
-----------------

##### Export data only
```
mysqldump --no-create-info ...
```

##### Export structure only
```
--no-data
```

##### Export without triggers
```
--skip-triggers
```

##### If using `--databases`, then include that
```
--no-create-db
```

##### Disable generate extended insert statements like
`INSERT INTO table_name VALUES (...), (...),  ...;`
```
--skip-extended-insert
```

##### More detail
```
man -k mysqldump
```

##### Reference Links
* http://stackoverflow.com/questions/5109993/mysqldump-data-only
* http://dba.stackexchange.com/questions/31598/mysql-duplicate-entry-error-1062-when-restoring-backup
* http://stackoverflow.com/questions/7622253/how-to-skip-row-when-importing-bad-mysql-dump


MySQL Query
-----------

##### Query in Random
```
SELECT * FROM table ORDER BY RAND();
```

##### Order by number in string
```
SELECT * FROM table ORDER BY fieldname+0;
```
```
SELECT * FROM table ORDER BY CAST(fieldname AS UNSIGNED);
```

##### Query in case-sensitive string
```
SELECT *  FROM table WHERE BINARY fieldname = value;
```

##### Create Database, User and Grant Privileges
```
CREATE DATABASE dbname CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE USER 'dbuser'@'localhost' IDENTIFIED BY 'db_password';
GRANT ALL PRIVILEGES ON dbname.* TO 'dbuser'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```


Change root Password
--------------------

##### MySQL 5.7.6 and later
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';
```

##### MySQL 5.7.5 and earlier
```
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('MyNewPass');
```
