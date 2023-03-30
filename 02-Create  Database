# Create Database
## 1. Create Schema
```
    CREATE SCHEMA <schema name>
		GO
```
## 2. Check all exist schema:
  Database\Security\Schemas
## 3. Create Table
```
    CREATE TABLE <Schemaname.tablename>
    GO
```
Example:
```
CREATE TABLE ProjectEmployee.Employee (
  EmployeeId int identity(1,1),
  EmployeeName varchar(500),
  Department varchar(500),
  DateOfJoining date,
  ProfileName varchar(500)  // Upload profile Picture profile url. Actual photo will store in server
)

```
## 4. Insert data into table

INSERT INTO <Schema name> . <Table name> (<Column 1 name> , <Column 2 name> ,....)
	VALUES 
		(<Column 1 value>, <Column 2 value>, ...),
    (<Column 1 value>, <Column 2 value>, ...),
    (<Column 1 value>, <Column 2 value>, ...),
    ...
    (<Column 1 value>, <Column 2 value>, ...);

Example:
```
INSERT INTO ProjectEmployee.Employee(EmployeeName, Department, DateOfJoining, ProfileName)
	VALUES 
		('Sam', 'IT', '2020-06-01', 'anonymous.png');

```
