# MySQL PhpMyAdmin

## Sql query to move data form one table to another and delete the data.

        INSERT INTO old_authors SELECT * FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-05-01";
        DELETE FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-05-01";

        SELECT added,DATE_FORMAT(added, "%Y-%m-%d") as new_date FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-05-01";

Another way to do this using Transaction

        START TRANSACTION;
        INSERT INTO old_authors SELECT * FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-04-24";
        DELETE FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-04-24";
        COMMIT;
        
## Fetch data from table gorup by dublicate data but fetch uniqly behalf of multipal group by
        
        SELECT recipient, events, tags, COUNT(events) AS CNT FROM tbl_email_logs WHERE tags REGEXP '^[0-9].*' GROUP BY recipient,events,tags HAVING COUNT(*) > 0;

## Count all dublicate data form table and delete duplicate data from table remains the last max id data on table

        SELECT , COUNT() AS CNT FROM mock_data GROUP BY gender HAVING COUNT(*) > 1;
        
        DELETE FROM mock_data WHERE id NOT IN ( SELECT MAX(id) AS MaxRecordID FROM mock_data GROUP BY gender );

## error: 1877 or #1030 - Got error 1877 "Unknown error" from storage engine InnoDB

Few points which might occure this error:

1. when create index in any db table it might currupt your table and then db engine like here `InnoDB` produce `1877` error.

   1. At first run these following `cmd command` to know is everything ok on `InnoDB` engin or not:

>>> Try to run `cmd` as `adminstrator`. If `cmd` not know this command that measns you need to add vraible in windows path like i am using windows in this case at first I need to find `mysql/bin` path and add this on `evniornment variable`. THis is my `bin` path: `E:\development\xampp\mysql\bin` . 
>>> Remeber in `cmd` at first go to the `bin` directory then run these commands other wise might be this will not run?

        mysqlcheck -r --all-databases

>>> In case this will produve validation error then run this 

        mysqlcheck -u root -p --check --all-databases

>>> u:user  p: password         
>>> This will provide you all avaialbae database related tables and there status with if have error or what type of error.

   1. After that try runnning this command to repair databasae

                mysqlcheck -u root -p --repair --all-databases

        or specific database using

                mysqlcheck -u root -p --repair --yourDataBaseName

        or specific table using

                REPAIR TABLE tableName

### Table engine or colletion not defined then:

If using `xampp server` and `phpmyadmin` then go to `phpmyadmin` and follow the steps:

1. open table and go to `operations` section.
1. In `operations` section you will look to `Table Opetions` section in which you get 
   1. `storange engine`
   1. `Collation`  
1. As per our problem assing `engine` and `collation` to table. 
