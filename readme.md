### interview prep queries

##### 1. find highest salary from emp table
###### 2nd highest

```
select max(salary) from emp_salary 
where
salary < (select max(salary) from emp_salary);
```
```
select max(salary) from emp_salary
where
salary not in (select max(salary) from emp_salary);
```
###### nth highest (n = 3)
select * from 
(select distinct(salary) from emp_salary order by salary desc limit 3)
as T
order by T.salary asc limit 1;
```