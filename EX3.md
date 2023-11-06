# EX 3 SubQueries, Views and Joins 
## DATE:

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
SELECT ENAME FROM EMP WHERE sal > (SELECT sal FROM emp WHERE empno = 7566);


### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/5cab28e8-079c-4ba4-b1fa-d5f94c95b566)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
SELECT ename,job,sal FROM emp WHERE sal = (SELECT MIN(sal) FROM emp);


### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/bf599918-a255-420a-ab84-d4868183fb0e)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
SELECT ename,job FROM emp WHERE deptno = 10 AND job IN (SELECT job FROM emp WHERE job = 'sales');


### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/d57e8ebd-d6ea-4166-9816-20df2c977795)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
CREATE VIEW empv AS SELECT empno,ename,job from emp WHERE deptno = 10;
SELECT ename FROM empv;


### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/6e77f7dc-c9f1-4367-87c9-545e1753ae9a)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
CREATE VIEW empv30 AS SELECT empno AS "Employee Number",ename AS "Emplo
yee Name",sal AS "Salary" from emp WHERE deptno = 30;
SELECT * FROM empv30;

### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/d577e234-1490-4ada-954c-0737e753939b)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
UPDATE empv SET sal = sal * 1.1 WHERE job = 'CLERK';


### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/13bc0700-373a-4817-b31d-5dfc0dfb7dfc)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
SELECT salesman.name AS "Salesman",customer1.cust_name AS "Customer Name",salesman.city AS "City" from salesman INNER JOIN customer1 ON salesman.city = customer1.city;

### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/7902ae3b-075f-4a0c-8944-2bc7d7f36343)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman.name AS "Salesman",salesman.commission AS "Commission" FROM salesman INNER JOIN customer1 ON salesman.salesman_id = customer1.salesman_id WHERE salesman.commission  > 0.13;


### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/8b50ed30-cc97-450f-9e43-8406a7294250)

### Q9) Perform Natural join on both tables

### QUERY:
SELECT * from customer1 natural join salesman;

### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/05b5ea09-4b50-4259-b722-005e4e3ce306)

### Q10) Perform Left and right join on both tables
#### LEFT JOIN:
### QUERY:
SELECT * FROM salesman LEFT JOIN customer1 ON salesman.salesman_id = customer1.salesman_id;

### OUTPUT:
![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/b77df71e-87f9-4fb3-8d1b-8be80431e710)
#### RIGHT JOIN:
### QUERY:
 SELECT * FROM salesman RIGHT JOIN customer1 ON salesman.salesman_id = customer1.salesman_id;
 ### OUTPUT:
 ![image](https://github.com/harini1006/EX-3-SubQueries-Views-and-Joins/assets/113497405/205c2d98-0c90-449b-a9ef-740d88ff215e)
