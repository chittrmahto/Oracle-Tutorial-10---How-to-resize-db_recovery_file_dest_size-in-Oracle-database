# Oracle-Tutorial-10---How-to-resize-db_recovery_file_dest_size-in-Oracle-database
Oracle Tutorial 10 - How to resize db_recovery_file_dest_size in Oracle database


Steps: ---
1. Login to your Oracle Database. (sqlplus / as sysdba) from command line.
2. run the below commands.

#Check Recovery File Dest Size
SQL> set lines 100
SQL>  col name format a60

SQL> select name, floor(space_limit / 1024 / 1024/1024) "Size GB", ceil(space_used / 1024 / 1024/1024)   "Used GB" from v$recovery_file_dest order by name;

NAME         Size GB      Used GB
------------------------------------------------------------ ----------
D:\app\Chirag\flash_recovery_area
                3            1
Here size is 3 GB and Used size is 1GB.

## Now Resize the DB_RECOVERY_FILE_DEST_SIZE
SQL> ALTER SYSTEM SET DB_RECOVERY_FILE_DEST_SIZE = 4G SCOPE=BOTH SID='*';

System altered.

### Again let me check the recover_file_dest_size;
SQL> select name, floor(space_limit / 1024 / 1024/1024) "Size GB", ceil(space_used / 1024 / 1024/1024)   "Used GB" from v$recovery_file_dest order by name;

NAME
        Size GB    Used GB
------------------------------------------------------------ ---------- ----------
D:\app\Chirag\flash_recovery_area
              4          1

##now new size is 4 GB.

If your are writing scope=Both then no need to restart the server.


Video URL : https://chittranjanmahto.blogspot.com/2019/09/oracle-tutorial-10-how-to-resize.html
