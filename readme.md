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
```
select * from 
(select distinct(salary) from emp_salary order by salary desc limit 3)
as T
order by T.salary asc limit 1;
```

#### 2. Display Alternate Records
##### columns: deptNo, salary, ename
```
select * from 
(select *, row_number() over (order by deptNo) as rownum from emp)
as T
where 
mod (rownum, 2) != 0;
```