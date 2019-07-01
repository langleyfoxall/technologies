# Langley Foxall Databases

## Platforms
### Web
Web applications will use [MySQL](https://www.mysql.com/) by default unless under exceptional circumstances and approved
by a lead developer.

Windows Stack applications will use MSSQL.

### UWP (Offline) 
UWP applications requiring offline functionality will use SQLite.

### iOS
iOS applications can either use CoreData OR Realm.

### Android
Android applications can use Realm.


### Approved Database Management Tools
Below are a list of approved database management tools that you can download and use.

* [Sequel Pro (Mac)](https://www.sequelpro.com/)
* [DataGrip (Universal)](https://www.jetbrains.com/datagrip/download/)
* [MySQL Workbench (Universal)](https://www.mysql.com/products/workbench/)
* [Realm Studio (Universal)](https://realm.io/products/realm-studio/)
* [TablePlus (Mac/ iOS)](https://tableplus.io/)
## Practices

### Identitys

ID's should be either auto-incrementing unsigned integers, or GUIDs/UUIDs. 

### Columns
Columns are to be defined in `snake_case` ONLY.

Columns that are relationships to other tables should reference the `id` column ideally. If the column references a 
record from the `users` table - it should be named `user_id`.

### Foreign keys
On all relationship columns, a foreign key (FK) should be defined.

This has a few benefits, such as the automatic indexing in MySQL and MariaDB.

```
Note: Indexes are NOT automatically created in PostgreSQL & Microsoft SQL Server. These should be added separately.
```

