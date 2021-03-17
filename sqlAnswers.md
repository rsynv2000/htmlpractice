# Answers

### Database Stuff

-   Database Name : `sqlpractice`
-   Table Names : `Student` and `Personal`
-   #### Tables Involved:

    -   ##### _Student_ Table

        | Roll | Sname   | Gender | Dob        | Total | Average | Grade |
        | ---- | ------- | ------ | ---------- | ----- | ------- | ----- |
        | 1    | Anand   | M      | 05/13/2001 | 407   | 81.4    | B     |
        | 2    | Ajay    | M      | 04/02/2001 | 400   | 80      | C     |
        | 3    | Bharath | M      | 11/05/2000 | 355   | 71      | D     |
        | 4    | Shivani | F      | 05/06/2001 | 476   | 95.2    | A     |
        | 5    | Sarchin | M      | 12/23/2001 | 400   | 80      | C     |
        | 6    | Dhoni   | M      | 11/17/2000 | 415   | 83      | B     |
        | 7    | Kamala  | F      | 12/05/2001 | 400   | 80      | C     |
        | 8    | Varun   | M      | 11/11/2000 | 470   | 94      | A     |
        | 9    | Rekha   | F      | 10/15/2000 | 490   | 98      | A     |

    -   ##### _Personal_ Table

        | Roll | Parent | Address          | Phone_No |
        | ---- | ------ | ---------------- | -------- |
        | 2    | ABC    | 1st Cross Street | 12345678 |
        | 3    | XYZ    | 2nd Cross Street | 41234561 |
        | 4    | PQR    | 3rd Cross Street | 12370171 |
        | 7    | LMN    | 4th Cross Street | 40007714 |
        | 9    | ABCD   | 5th Cross Street | 56789101 |

-   This the command to create the `Student` table:

    ```sql
        CREATE TABLE Student(
            Roll INT NOT NULL,
            Sname char(15),
            Gender char(2),
            Dob DATE,
            Total INT,
            Average NUMERIC(10, 2),
            Grade char(2)
        );
    ```

-   Inserting multiple values into the `Student` table at the same time:

    ```sql
        INSERT INTO `Student`
            (`Roll`, `Sname`, `Gender`, `Dob`, `Total`, `Average`, `Grade`)
        VALUES
            (1, 'Anand', 'M', '2001-05-13', 407, '81.40', 'B'),
            (2, 'Ajay', 'M', '2001-04-02', 400, '80.00', 'C'),
            (3, 'Bharath', 'M', '2000-11-05', 355, '71.00', 'D'),
            (4, 'Shivani', 'F', '2001-05-06', 476, '95.20', 'A'),
            (5, 'Sarchin', 'M', '2001-12-23', 400, '80.00', 'C'),
            (6, 'Dhoni', 'M', '2000-11-17', 415, '83.00', 'B'),
            (7, 'Kamala', 'F', '2001-12-05', 400, '80.00', 'C'),
            (8, 'Varun', 'M', '2000-11-11', 470, '94.00', 'A'),
            (9, 'Rekha', 'F', '2000-10-15', 490, '98.00', 'A');
    ```

-   This the command to create the `Personal` table:

    ```sql
        CREATE TABLE Personal(
            Roll INT,
            Parent char(10),
            Address CHAR(20),
            Phone_No CHAR(10)
        );
    ```

-   Inserting multiple values into the `Personal` table at the same time:

    ```sql
        INSERT INTO `Personal`
            (`Roll`, `Parent`, `Address`, `Phone_No`)
        VALUES
            (2, 'ABC', '1st Cross Street', '12345678'),
            (3, 'XYZ', '2nd Cross Street', '41234561'),
            (4, 'PQR', '3rd Cross Street', '12370171'),
            (7, 'LMN', '4th Cross Street', '40007714'),
            (9, 'ABCD', '5th Cross Street', '56789101');
    ```

### Q01. Display name and gender of all the students.

#### _Answer :_

##### _Query_ :

```sql
    SELECT Sname, Gender
    FROM `Student`;
```

##### _Output_ :

```
+---------+--------+
|  Sname  | Gender |
+---------+--------+
| Anand   | M      |
| Ajay    | M      |
| Bharath | M      |
| Shivani | F      |
| Sarchin | M      |
| Dhoni   | M      |
| Kamala  | F      |
| Varun   | M      |
| Rekha   | F      |
+---------+--------+
```

<hr>

### Q02. Display the contents of the entire table.

#### _Answer :_

##### _Query_ :

```sql
 select * from Student;
```

##### _Output_ :

```
+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |
+------+---------+--------+------------+-------+---------+-------+
|    1 | Anand   | M      | 2001-05-13 |   407 |   81.40 | B     |
|    2 | Ajay    | M      | 2001-04-02 |   400 |   80.00 | C     |
|    3 | Bharath | M      | 2000-11-05 |   355 |   71.00 | D     |
|    4 | Shivani | F      | 2001-05-06 |   476 |   95.20 | A     |
|    5 | Sarchin | M      | 2001-12-23 |   400 |   80.00 | C     |
|    6 | Dhoni   | M      | 2000-11-17 |   415 |   83.00 | B     |
|    7 | Kamala  | F      | 2001-12-05 |   400 |   80.00 | C     |
|    8 | Varun   | M      | 2000-11-11 |   470 |   94.00 | A     |
|    9 | Rekha   | F      | 2000-10-15 |   490 |   98.00 | A     |
+------+---------+--------+------------+-------+---------+-------+
```

<hr>

### Q03. Display the unique values of `Total` from the table.

#### _Answer :_

##### _Query_ :

```sql
select distinct Total from student;
```

##### _Output_ :

```
+-------+
| Total |
+-------+
|   407 |
|   400 |
|   355 |
|   476 |
|   415 |
|   470 |
|   490 |
+-------+
```

<hr>

### Q04. Display roll number and name of the male students.

#### _Answer :_

##### _Query_ :

```sql
select Roll,Sname from student where Gender='M';
```

##### _Output_ :

```
+------+---------+
| Roll | Sname   |
+------+---------+
|    1 | Anand   |
|    2 | Ajay    |
|    3 | Bharath |
|    5 | Sarchin |
|    6 | Dhoni   |
|    8 | Varun   |
+------+---------+
```

<hr>

### Q05. Display the roll number and name of male students who have scored above 400.

#### _Answer :_

##### _Query_ :

```sql
SELECT Roll,Sname FROM Student WHERE Total>400 AND Gender='M';
```

##### _Output_ :

```
+------+-------+
| Roll | Sname |
+------+-------+
|    1 | Anand |
|    6 | Dhoni |
|    8 | Varun |
+------+-------+
```

<hr>

### Q06. Display the details of students who have scored between 400 and 450. (Limits inclusive)

#### _Answer :_

##### _Query_ :

```sql
select * from student where Total between 400 and 450;
```

##### _Output_ :

```
+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |  
+------+---------+--------+------------+-------+---------+-------+  
|    1 | Anand   | M      | 2001-05-13 |   407 |   81.40 | B     |
|    2 | Ajay    | M      | 2001-04-02 |   400 |   80.00 | C     |  
|    5 | Sarchin | M      | 2001-12-23 |   400 |   80.00 | C     |  
|    6 | Dhoni   | M      | 2000-11-17 |   415 |   83.00 | B     |  
|    7 | Kamala  | F      | 2001-12-05 |   400 |   80.00 | C     |  
+------+---------+--------+------------+-------+---------+-------+ 
```

<hr>

### Q07. Display details of male students who have scored between 400 and 450.

#### _Answer :_

##### _Query_ :

```sql
SELECT * FROM Student WHERE Gender='M' AND Total BETWEEN 400 AND 450;
```

##### _Output_ :

```
+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |  
+------+---------+--------+------------+-------+---------+-------+  
|    1 | Anand   | M      | 2001-05-13 |   407 |   81.40 | B     |  
|    2 | Ajay    | M      | 2001-04-02 |   400 |   80.00 | C     |  
|    5 | Sarchin | M      | 2001-12-23 |   400 |   80.00 | C     |  
|    6 | Dhoni   | M      | 2000-11-17 |   415 |   83.00 | B     |
+------+---------+--------+------------+-------+---------+-------+ 
```

<hr>

### Q08. Display names of students who have scored the grades A, B or C from the table.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where Grade='A' or 
Grade='B' or Grade='c';
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Anand   |
| Ajay    |
| Shivani |
| Sarchin |
| Dhoni   |
| Kamala  |
| Varun   |
| Rekha   |
+---------+
```

<hr>

### Q09. Display the name of female students who have scored the grades A or B.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where Gender='F' and (Grade='A' or Grade='B');
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Shivani |
| Rekha   |
+---------+
```

<hr>

### Q10. Display the roll numbers of students who have scored grade other than A or B.

#### _Answer :_

##### _Query_ :

```sql
select Roll from Student where Grade!='A' and Grade!='B';
```

##### _Output_ :

```
+------+
| Roll |
+------+
|    2 |
|    3 |
|    5 |
|    7 |
+------+
```

<hr>

### Q11. Display the names of the students born in the year 2001.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where year(Dob)="2001";
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Anand   |
| Ajay    |
| Shivani |
| Sarchin |
| Kamala  |
+---------+
```

<hr>

### Q12. Display the names of the students born in the month of November 2000.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where year(Dob)='2000' and month(Dob)='11';
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Bharath |
| Dhoni   |
| Varun   |
+---------+
```

<hr>

### Q13. Display the names of the students born in the year 2000 but not in the month of November.

#### _Answer :_

##### _Query_ :

```sql
 select Sname from Student where year(Dob)='2000' and month(Dob)!='11';
```

##### _Output_ :

```
+-------+
| Sname |
+-------+
| Rekha |
+-------+
```

<hr>

### Q14. Display the different grades obtained by the students.

#### _Answer :_

##### _Query_ :

```sql
select distinct Grade from student;
```

##### _Output_ :

+-------+
| Grade |
+-------+
| B     |
| C     |
| D     |
| A     |
+-------+```

```

<hr>

### Q15. Display the name, average and grade of all female students in the following format:

```
Shivani has scored an average of 95.2 with grade A.
```

#### _Answer :_

##### _Query_ :

```sql
select concat(Sname,' has scored an average of ',Average,' with grade ',Grade,'.') as 'Progress Of Female Students' from student where Gender='F';
```

##### _Output_ :

```
+------------------------------------------------------+
| Progress Of Female Students                          |
+------------------------------------------------------+
| Shivani has scored an average of 95.20 with grade A. |
| Kamala has scored an average of 80.00 with grade C.  |
| Rekha has scored an average of 98.00 with grade A.   |
+------------------------------------------------------+
```

<hr>

### Q16. Assume there is no average column in the table and the Total attribute is the expression of 5 subjects mark. Display the name and average marks of all the female students.

#### _Answer :_

##### _Query_ :

```sql
select Sname , Total/5 as 'Average' from student where Gender='F';
```

##### _Output_ :

```
+---------+---------+
| Sname   | Average |
+---------+---------+
| Shivani | 95.2000 |
| Kamala  | 80.0000 |
| Rekha   | 98.0000 |
+---------+---------+
```

<hr>

### Q17. Display names of students whose name starts with 'A'.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where Sname like 'A%';
```

##### _Output_ :

```
+-------+
| Sname |
+-------+
| Anand |
| Ajay  |
+-------+
```

<hr>

### Q18. Display the roll number, name, total of the students whose starts with 'A' and ends with 'd'.

#### _Answer :_

##### _Query_ :

```sql
select roll,sname,Total from Student where Sname like 'A%' and Sname like '%d';
```

##### _Output_ :

```
+------+-------+-------+
| roll | sname | Total |
+------+-------+-------+
|    1 | Anand |   407 |
+------+-------+-------+
```

<hr>

### Q19. Display the details of students whose name is exactly 5 charcters in length.

#### _Answer :_

##### _Query_ :

```sql
select * from student where length(Sname)=5;
```

##### _Output_ :

```
+------+-------+--------+------------+-------+---------+-------+
| Roll | Sname | Gender | Dob        | Total | Average | Grade |
+------+-------+--------+------------+-------+---------+-------+
|    1 | Anand | M      | 2001-05-13 |   407 |   81.40 | B     |
|    6 | Dhoni | M      | 2000-11-17 |   415 |   83.00 | B     |
|    8 | Varun | M      | 2000-11-11 |   470 |   94.00 | A     |
|    9 | Rekha | F      | 2000-10-15 |   490 |   98.00 | A     |
+------+-------+--------+------------+-------+---------+-------+
```

<hr>

### Q20. Display the details of students whose name has 'i'.

#### _Answer :_

##### _Query_ :

```sql
select * from Student where Sname like '%i%';
```

##### _Output_ :

```
+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |
+------+---------+--------+------------+-------+---------+-------+
|    4 | Shivani | F      | 2001-05-06 |   476 |   95.20 | A     |
|    5 | Sarchin | M      | 2001-12-23 |   400 |   80.00 | C     |
|    6 | Dhoni   | M      | 2000-11-17 |   415 |   83.00 | B     |
+------+---------+--------+------------+-------+---------+-------+
```

<hr>

### Q21. Display the names of students not starting with A or S.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where Sname not like 'A%' and Sname not like 'S%';
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Bharath |
| Dhoni   |
| Kamala  |
| Varun   |
| Rekha   |
+---------+
```

<hr>

### Q22. Display names of students whose birth date is 5.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student where day(Dob)='05';
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Bharath |
| Kamala  |
+---------+
```

<hr>

### Q23. Display the names of students in the table in alphabetical order.

#### _Answer :_

##### _Query_ :

```sql
select Sname from Student order by Sname;  
```

##### _Output_ :

```
+---------+
| Sname   |
+---------+
| Ajay    |
| Anand   |
| Bharath |
| Dhoni   |
| Kamala  |
| Rekha   |
| Sarchin |
| Shivani |
| Varun   |
+---------+
```

<hr>

### Q24. Display the name and total of female students in descending order of total.

#### _Answer :_

##### _Query_ :

```sql
 select Sname,Total from Student where Gender='F' order by Total desc;
```

##### _Output_ :

```
+---------+-------+
| Sname   | Total |
+---------+-------+
| Rekha   |   490 |
| Shivani |   476 |
| Kamala  |   400 |
+---------+-------+
```

<hr>

### Q25. Display the name, grade and total of all the students who have scored above 395 in descending order of their grades and ascending order of their name.

#### _Answer :_

##### _Query_ :

```sql
select Sname,Grade,Total from Student where Total>395 order by Grade desc,Sname asc;
```

##### _Output_ :

```
+---------+-------+-------+
| Sname   | Grade | Total |
+---------+-------+-------+
| Ajay    | C     |   400 |
| Kamala  | C     |   400 |
| Sarchin | C     |   400 |
| Anand   | B     |   407 |
| Dhoni   | B     |   415 |
| Rekha   | A     |   490 |
| Shivani | A     |   476 |
| Varun   | A     |   470 |
+---------+-------+-------+
```

<hr>

### Q26. Find the sum of the total marks obtained by students who have scored the grade 'A'.

#### _Answer :_

##### _Query_ :

```sql
select sum(Total) from Student where Grade="A";
```

##### _Output_ :

```
+------------+
| sum(Total) |
+------------+
|       1436 |
+------------+
```

<hr>

### Q27. Display the average of the average marks scored by 'A' graders.

#### _Answer :_

##### _Query_ :

```sql
select avg(Average) from Student where Grade='A';
```

##### _Output_ :

```
+--------------+
| avg(Average) |
+--------------+
|    95.733333 |
+--------------+
```

<hr>

### Q28. Display the total number of students in the table.

#### _Answer :_

##### _Query_ :

```sql
select count(Roll) from student;
```

##### _Output_ :

```
+-------------+
| count(Roll) |
+-------------+
|           9 |
+-------------+
```

<hr>

### Q29. Display the number of different grades available in the table.

#### _Answer :_

##### _Query_ :

```sql
select count(distinct(Grade)) from Student;
```

##### _Output_ :

```
+------------------------+
| count(distinct(Grade)) |
+------------------------+
|                      4 |
+------------------------+
```

<hr>

### Q30. Display the details of the student(s) who is the youngest in the table.

#### _Answer :_

##### _Query_ :

```sql
select * from Student where Dob in (SELECT MAX(Dob) FROM Student);
```

##### _Output_ :

```
+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |  
+------+---------+--------+------------+-------+---------+-------+  
|    5 | Sarchin | M      | 2001-12-23 |   400 |   80.00 | C     |  
+------+---------+--------+------------+-------+---------+-------+  
```

<hr>

### Q31. Write the Output for the following

#### Q31.1

```sql
    SELECT MAX(Dob), MIN(Dob), SUM(Total)
    FROM `Student`
    WHERE Dob BETWEEN '2001-01-01' AND '2001-12-31';
```

#### _Answer :_

##### _Output_ :

```
+------------+------------+------------+
| MAX(Dob)   | MIN(Dob)   | SUM(Total) |
+------------+------------+------------+
| 2001-12-23 | 2001-04-02 |       2083 |
+------------+------------+------------+
```

#### Q31.2

```sql
    SELECT COUNT(*), MAX(Total), MIN(Total)
    FROM `Student`
    WHERE Grade IN ('A', 'B');
```

#### _Answer :_

##### _Output_ :

```
+----------+------------+------------+
| COUNT(*) | MAX(Total) | MIN(Total) |
+----------+------------+------------+
|        5 |        490 |        407 |
+----------+------------+------------+
```

#### Q31.3

```sql
    SELECT SUM(Total + 5)
    FROM `Student`
    WHERE Grade='D';
```

#### _Answer :_

##### _Output_ :

```
+----------------+
| SUM(Total + 5) |
+----------------+
|            360 |
+----------------+
```

#### Q31.4

```sql
    SELECT AVG(Total / 5)
    FROM `Student`;
```

#### _Answer :_

##### _Output_ :

```
+----------------+
| AVG(Total / 5) |
+----------------+
|    84.73333333 |
+----------------+
```

<hr>

### Q32. Display the count of gender based on gender.

#### _Answer :_

##### _Query_ :

```sql
elect count(Gender),sum(Gender='M'),sum(Gender='F') from Student;
```

##### _Output_ :

```
+---------------+-----------------+-----------------+
| count(Gender) | sum(Gender='M') | sum(Gender='F') |
+---------------+-----------------+-----------------+
|             9 |               6 |               3 |
+---------------+-----------------+-----------------+
```

<hr>

### Q33. Display the maximum and minimum marks obtained by the students grade wise.

#### _Answer :_

##### _Query_ :

```sql
select max(Total),min(Total), Grade from Student group by Grade;
```

##### _Output_ :

```
+------------+------------+-------+
| max(Total) | min(Total) | Grade |
+------------+------------+-------+
|        490 |        470 | A     |
|        415 |        407 | B     |
|        400 |        400 | C     |
|        355 |        355 | D     |
+------------+------------+-------+
```

<hr>

### Q34. Display the maximum and minimum total of the students born in the year 2001 based on their grade.

#### _Answer :_

##### _Query_ :

```sql
select Grade,max(Total),min(Total) from student where year(Dob)=2001 group by Grade;
```

##### _Output_ :

```
+-------+------------+------------+
| Grade | max(Total) | min(Total) |
+-------+------------+------------+
| A     |        476 |        476 |
| B     |        407 |        407 |
| C     |        400 |        400 |
+-------+------------+------------+
```

<hr>

### Q35. Display the number of students grade wise where grades include A and B.

#### _Answer :_

##### _Query_ :

```sql
select Grade,count(Roll) from Student where Grade='A' or Grade='B' group by Grade;
```

##### _Output_ :

```
+-------+-------------+
| Grade | count(Roll) |
+-------+-------------+
| A     |           3 |
| B     |           2 |
+-------+-------------+
```

<hr>

### Q36. Display the number of students grade wise where number of students in each grade is more than two.

#### _Answer :_

##### _Query_ :

```sql
select Grade, count(Grade) from Student group by Grade having count(Grade)>2;
```

##### _Output_ :

```
+-------+--------------+
| Grade | count(Grade) |
+-------+--------------+
| A     |            3 |
| C     |            3 |
+-------+--------------+
```

<hr>

### Q37. Update Varun's date of birth to 12th November 2000.

#### _Answer :_

##### _Query_ :

```sql
update Student set Dob='2000-11-12' where Sname='Varun';

select * from Student where Sname='Varun';
```

##### _Output_ :

```
Query OK, 1 row affected, 1 warning (0.152 sec)
Rows matched: 1  Changed: 1  Warnings: 1

 +------+-------+--------+------------+-------+---------+-------+
| Roll | Sname | Gender | Dob        | Total | Average | Grade |    
+------+-------+--------+------------+-------+---------+-------+    
|    8 | Varun | M      | 2000-11-12 |   470 |   94.00 | A     |    
+------+-------+--------+------------+-------+---------+-------+
```

<hr>

### Q38. Increment Sarchin's mark by 10 and alter his grade to B.

#### _Answer :_

##### _Query_ :

```sql
update student set Total=Total+10, Grade='B' 
where Sname='Sarchin';

select * from Student where Sname='Sarchin';
```

##### _Output_ :

```
where Sname='Sarchin';
Query OK, 1 row affected (0.132 sec)
Rows matched: 1  Changed: 1  Warnings: 0


+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |  
+------+---------+--------+------------+-------+---------+-------+  
|    5 | Sarchin | M      | 2001-12-23 |   410 |   80.00 | B     |
+------+---------+--------+------------+-------+---------+-------+
```

<hr>

### Q39. Create a view V1 which is an exact copy of the _Student_ table. Display it after creation.

Note: 2 seperate queries to be executed. One for the view and another for the displaying part.

#### _Answer :_

##### _Query_ :

```sql
create view v1 as select * from student;

v
```

##### _Output_ :

```
Query OK, 0 rows affected


+------+---------+--------+------------+-------+---------+-------+
| Roll | Sname   | Gender | Dob        | Total | Average | Grade |  
+------+---------+--------+------------+-------+---------+-------+  
|    1 | Anand   | M      | 2001-05-13 |   407 |   81.40 | B     |  
|    2 | Ajay    | M      | 2001-04-02 |   400 |   80.00 | C     |  
|    3 | Bharath | M      | 2000-11-05 |   355 |   71.00 | D     |  
|    4 | Shivani | F      | 2001-05-06 |   476 |   95.20 | A     |  
|    5 | Sarchin | M      | 2001-12-23 |   410 |   80.00 | B     |  
|    6 | Dhoni   | M      | 2000-11-17 |   415 |   83.00 | B     |  
|    7 | Kamala  | F      | 2001-12-05 |   400 |   80.00 | C     |  
|    8 | Varun   | M      | 2000-11-12 |   470 |   94.00 | A     |  
|    9 | Rekha   | F      | 2000-10-15 |   490 |   98.00 | A     |  
+------+---------+--------+------------+-------+---------+-------+ 

```

<hr>

### Q40. Create a view V2 which contains roll number and name of all the 'A' graders.

#### _Answer :_

##### _Query_ :

```sql
create view V2 as select Roll,Sname from Student where Grade='A';
```

##### _Output_ :

```
Query OK, 0 rows affected
```

<hr>

### Q41. Display the contents of the new view V2.

#### _Answer :_

##### _Query_ :

```sql
select * from V2;
```

##### _Output_ :

```
+------+---------+
| Roll | Sname   |
+------+---------+
|    4 | Shivani |
|    8 | Varun   |
|    9 | Rekha   |
+------+---------+
```

<hr>

### Q42. Create a view V3 that has a a copy of roll number and name of all the 'A' graders but with new column names. Display the view after creation.

Note: 2 seperate queries to be executed. One for the view and another for the displaying part.

#### _Answer :_

##### _Query_ :

```sql
create view v3 as select Roll as RollNo,Sname as Name from Student where Grade='A';

select * from v3;
```

##### _Output_ :

```
Query OK, 0 rows affected


+--------+---------+
| RollNo | Name    |
+--------+---------+
|      4 | Shivani |
|      8 | Varun   |
|      9 | Rekha   |
+--------+---------+

```

<hr>

### Q43. Add a new column age of appropriate data type to the existing table and fill the age.

Note: First you will be adding a the column. Then you will be calculating the age and updating it in the table. So, 2 separate queries. Have the output of both the queries.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q44. Remove the column age from the _Student_ table.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q45. Alter the Average column to FLOAT(10, 2).

Note:

-   Before executing the query for this question, execute `DESC Student;` and have the output in the markdown file.
-   Display the `Student` Table.
-   Have the query and the output for that in the markdown file.
-   Execute the query to change the column type.
-   Paste the query and the output to the markdown file.
-   Execute `DESC Student;` and paste the output in the markdown file.
-   Display the `Student` table again.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q46. Display the value of Total / 5 for every female student and give a new column name.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q47. Display the student name, parent name and address of all the students.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q48. Display the roll number, student name and parent name of all 'A' graders.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q49. Remove the details of those students from the `Student` table who have got 'D' grade.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>

### Q50. Remove the Student table from the database.

#### _Answer :_

##### _Query_ :

```sql

```

##### _Output_ :

```

```

<hr>
