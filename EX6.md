# Ex. No: 6 Creating Cursors using PL/SQL

### AIM: To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
```ruby
DEVELOPED BY : KULASEKARAPANDIAN K
REGISTER NO : 212222240052
DEVELOPED IN: MySQL Workbench
```

### Create employee table
```sql
CREATE TABLE employee (
    empid INT,
    empname VARCHAR(19),
    dept VARCHAR(10),
    salary INT
);
```

#### Insert values:
```sql
INSERT INTO employee VALUES (101, 'kulasekarapandian', 'AIML', 100000);
INSERT INTO employee VALUES (102, 'aravind', 'AIDS', 200000);
INSERT INTO employee VALUES (103, 'imthiyas', 'AIDS', 200000);
```

### PLSQL Cursor code
```sql
DELIMITER //
CREATE PROCEDURE DisplayEmployees()
BEGIN
    DECLARE done INT DEFAULT FALSE;
    DECLARE emp_id INT;
    DECLARE emp_name VARCHAR(19);
    DECLARE emp_dept VARCHAR(10);
    DECLARE emp_salary INT;
    DECLARE employee_cursor CURSOR FOR
        SELECT empid, empname, dept, salary FROM employee;
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    OPEN employee_cursor;
    read_loop: LOOP
        FETCH employee_cursor INTO emp_id, emp_name, emp_dept, emp_salary;
        IF done THEN
            LEAVE read_loop;
        END IF;
        SELECT emp_id, emp_name, emp_dept, emp_salary;
    END LOOP;
    CLOSE employee_cursor;
END //
DELIMITER ;
```

### CALL Function:
```sql
CALL DisplayEmployees();
```
### Output:

##### Output 1:
![OUTPUT](/result1.png)

##### Output 2:
![OUTPUT](/result2.png)

##### Output 3:
![OUTPUT](/result3.png)

### Result:
THE PROGRAM HAS BEEN IMPLEMENTED SUCCESSFULLY.
