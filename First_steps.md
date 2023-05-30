### First steps in MySQL  
#### Install MySQL
Our Server  
#### Install MySQL workbench
A Client of a MySQL Server for database design, modelling, creation, manipulation, maintenance, administration. More of an IDE
### The Client-Server Model  
![query_arch](img/client_server.png)  
### Creating a Database  

```
CREATE DATABASE [IF NOT EXISTS] database_name;
```  
```[IF NOT EXISTS]```
Verifies if a database with the same name exists already - It's optinal though  
*The SQL code is not case sensitive*  

### Creating Table
```CREATE DATABASE [IF NOT EXISTS] sales;
   CREATE TABLE table_name ( );
```
*You should add atleast one column when creating a table*  
