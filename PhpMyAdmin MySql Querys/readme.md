# Sql query to move data form one table to another and delete the data.

        INSERT INTO old_authors SELECT * FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-05-01";
        DELETE FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-05-01";

        SELECT added,DATE_FORMAT(added, "%Y-%m-%d") as new_date FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-05-01";

Another way to do this using Transaction

        START TRANSACTION;
        INSERT INTO old_authors SELECT * FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-04-24";
        DELETE FROM authors WHERE DATE_FORMAT(added, "%Y-%m-%d") > "2022-04-24";
        COMMIT;
