## Final Lab Task 2 : Transforming ER Model to Relational Tables

## Task Description: 
Given the ER diagram representing student assignment submissions, convert it into MySQL
tables. Capture all entities and their attributes, and define the relationships between students,
submissions, and assignments. Identify the primary and foreign keys and ensure proper representation of any dependent or weak entities.  

## REQUIRED OUTPUT
1. Query statements (Task 1-4 including the table relationship)
2. Table Structure (Task 1- 4 including the table relationship)
3. ER Diagram or Relational schema from phpMyAdmin or Workbench (pdf or jpg file)
4. Sql copy of the database and table structures
## STEP 1:
- Open XAMPP and start the Apatche and MySQL then open MySQL workbench
- Add a new connection
- Click the connection made
## STEP 2:
- Create a DATABASE BY using  
 `CREATE DATABASE database_name`
- Use the database that has created by using  
  `USE database_name`
### Type the following data types attributes
- student table: 
 - username: String (VARCHAR), up to 50 characters. 
- assignment table: 
 - shortname: String (VARCHAR), up to 50 characters. 
 - due_date: Date, cannot be null. 
 - url: String (VARCHAR), up to 255 characters, can be null. 
- submission table: 
 - username: String (VARCHAR), up to 50 characters. 
 - shortname: String (VARCHAR), up to 50 characters. 
 - version: Integer, represents the version of the submission. 
 - submit_date: Date, cannot be null. 
 - data: Text.,
- Creating Student Table  
`CREATE TABLE student_tbl(username VARCHAR(50)PRIMARY KEY NOT NULL UNIQUE);`
#### TABLE STRUCTURE AND QUERY STATEMENT
![](image/25fff43b-4f3e-42bb-9903-b440bb0183d0%20-%20Copy.jfif)

- Creating Submission Table  
` username VARCHAR(50), FOREIGN KEY (username) REFERENCES student_tbl(username), shortname VARCHAR(50), FOREIGN KEY(shortname) REFERENCES assignment_tbl(shortname) ON DELETE CASCADE
ON UPDATE CASCADE, version INT NOT NULL, submit_date DATE NOT NULL, data TEXT, PRIMARY KEY(username, shortname, version));`
#### TABLE STRUCTURE AND QUERY STATEMENT
![](image/1ae112cf-bdea-4651-9f37-6cba0dcea30a.jfif)

- Creating Assignment Table  
`CREATE TABLE assignment_tbl (shortname  VARCHAR(50) NOT NULL PRIMARY KEY , due_date DATE NOT NULL, url VARCHAR(255) UNIQUE);`
#### TABLE STRUCTURE AND QUERY STATEMENT
![](image/7e00517e-2352-420a-945b-9e5cbd260880.jfif)

### HERE IS THE ER Diagram OR Relational schema
![](image/0c57f87f-2aff-40b2-bb5d-eddc45cec060.jfif)


#### HERE IS THE MYSQL FILE
[Student Table](file/assignment_submission_student_tbl%20(1).sql)  
[Submission Table](file/assignment_submission_submission_tbl%20(1).sql)  
[Assignment Table](file/assignment_submission_assignment_tbl%20(1).sql)  
