#1 Create a list of students showing first and last names only.
    mysql> select first_name, last_name
        -> from student;
    +------------+-----------+
    | first_name | last_name |
    +------------+-----------+
    | Brian      | Biggs     |
    | Eric       | Ephram    |
    | Greg       | Gould     |
    | Adam       | Ant       |
    | Howard     | Hess      |
    | Charles    | Caldwell  |
    | James      | Joyce     |
    | Doug       | Dumas     |
    | Kevin      | Kraft     |
    | Frank      | Fountain  |
    +------------+-----------+
    10 rows in set (0.00 sec)

#2 Create a list of students with all the columns but only if the student has less than 8 years experience
    mysql> select *
        -> from student
        -> where years_of_experience < 8;
    +------------+------------+-----------+---------------------+------------+
    | student_id | first_name | last_name | years_of_experience | start_date |
    +------------+------------+-----------+---------------------+------------+
    |          1 | Brian      | Biggs     |                   4 | 2015-12-25 |
    |          2 | Eric       | Ephram    |                   2 | 2016-03-31 |
    |          3 | Greg       | Gould     |                   6 | 2016-09-30 |
    |          4 | Adam       | Ant       |                   5 | 2016-06-02 |
    |          5 | Howard     | Hess      |                   1 | 2016-02-28 |
    |          6 | Charles    | Caldwell  |                   7 | 2016-05-07 |
    |          9 | Kevin      | Kraft     |                   3 | 2016-04-15 |
    +------------+------------+-----------+---------------------+------------+
    7 rows in set (0.00 sec)


#3 Create a list of students showing the lastname, startdate, and id columns only and sorted by last_name in ascending sequence
    mysql> select last_name, start_date, student_id
        -> from student
        -> order by last_name;
    +-----------+------------+------------+
    | last_name | start_date | student_id |
    +-----------+------------+------------+
    | Ant       | 2016-06-02 |          4 |
    | Biggs     | 2015-12-25 |          1 |
    | Caldwell  | 2016-05-07 |          6 |
    | Dumas     | 2016-07-04 |          8 |
    | Ephram    | 2016-03-31 |          2 |
    | Fountain  | 2016-01-31 |         10 |
    | Gould     | 2016-09-30 |          3 |
    | Hess      | 2016-02-28 |          5 |
    | Joyce     | 2016-08-27 |          7 |
    | Kraft     | 2016-04-15 |          9 |
    +-----------+------------+------------+
    10 rows in set (0.00 sec)



#4 Create a list of students showing all columns but only if the student first name is Adam, James, or Frank and sort them in last_name descending sequence.
    mysql> select *
        -> from student
        -> where first_name in ('Adam', 'James', 'Frank');
    +------------+------------+-----------+---------------------+------------+
    | student_id | first_name | last_name | years_of_experience | start_date |
    +------------+------------+-----------+---------------------+------------+
    |          4 | Adam       | Ant       |                   5 | 2016-06-02 |
    |          7 | James      | Joyce     |                   9 | 2016-08-27 |
    |         10 | Frank      | Fountain  |                   8 | 2016-01-31 |
    +------------+------------+-----------+---------------------+------------+
    3 rows in set (0.00 sec)



#5 Create a list of students showing firstname, lastname and startdate where the startdate is between Jan 1, 2016 and June 30, 2016 and order the list by descending start_date sequence.
    mysql> select first_name, last_name, start_date
        -> from student
        -> where start_date > '2016-01-01'
        -> and start_date < '2016-06-30'
        -> order by start_date desc;
    +------------+-----------+------------+
    | first_name | last_name | start_date |
    +------------+-----------+------------+
    | Adam       | Ant       | 2016-06-02 |
    | Charles    | Caldwell  | 2016-05-07 |
    | Kevin      | Kraft     | 2016-04-15 |
    | Eric       | Ephram    | 2016-03-31 |
    | Howard     | Hess      | 2016-02-28 |
    | Frank      | Fountain  | 2016-01-31 |
    +------------+-----------+------------+
    6 rows in set (0.00 sec)



#Medium challenge questions: Explains & Selects

mysql> describe assignment
    -> ;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| student_id     | int(11) unsigned | NO   | MUL | NULL    |                |
| grade_id       | int(10) unsigned | NO   | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> select * from assignment
    -> ;
+---------------+----------------+----------+------------+----------+
| assignment_id | assignment_nbr | class_id | student_id | grade_id |
+---------------+----------------+----------+------------+----------+
|             1 |              1 |        5 |          1 |        1 |
|             2 |              2 |        5 |          1 |        2 |
|             3 |              3 |        5 |          1 |        5 |
|             4 |              1 |        5 |          2 |        4 |
|             5 |              2 |        5 |          2 |        3 |
|             6 |              3 |        5 |          2 |        2 |
+---------------+----------------+----------+------------+----------+
6 rows in set (0.00 sec)

mysql> describe grade;
+-------------+------------------+------+-----+---------+----------------+
| Field       | Type             | Null | Key | Default | Extra          |
+-------------+------------------+------+-----+---------+----------------+
| grade_id    | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| grade_value | char(30)         | NO   |     | NULL    |                |
+-------------+------------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)

mysql> select * from grade;
+----------+-----------------------------+
| grade_id | grade_value                 |
+----------+-----------------------------+
|        1 | Incomplete                  |
|        2 | Complete and unsatisfactory |
|        3 | Complete and satisfactory   |
|        4 | Exceeds expectations        |
|        5 | Not graded                  |
+----------+-----------------------------+
5 rows in set (0.00 sec)


#Hard

mysql> insert into assignment values
    -> (7, 4, 5, 1, 3);
Query OK, 1 row affected (0.00 sec)

# Fails to insert due to student_id constraint
mysql> insert into assignment values
    -> (8, 4, 5, 15, 2);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`tiy`.`assignment`, CONSTRAINT `fk_student_id` FOREIGN KEY (`student_id`) REFERENCES `student` (`student_id`))
mysql>


mysql> insert into assignment values
    -> (8, 4, 5, 5, 2);
Query OK, 1 row affected (0.00 sec)

# Fails to insert due to grade_id constraint
mysql> insert into assignment values
    -> (9, 1, 5, 5, 7);
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`tiy`.`assignment`, CONSTRAINT `fk_grade_id` FOREIGN KEY (`grade_id`) REFERENCES `grade` (`grade_id`))
mysql>
