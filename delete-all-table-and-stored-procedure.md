## Database Table & Stored Procedure Delete All (Clean Database)
```
use [database_name]
-- drop all tables
EXEC sp_MSforeachtable @Command1 = "DROP TABLE ?"
```
## Drop all user defined stored procedures
```
use [database_name]
Declare @procname varchar(500)
Declare cur Cursor For Select [name] From sys.objects where type = 'p'
Open cur
Fetch Next From cur Into @procname
While @@fetch_status = 0
Begin
Exec('drop procedure ' + @procname)
Fetch Next From cur Into @procname
End
Close cur
Deallocate cur
```
