<h1 align="center">Database</h1>
Data -> PROCESS -> Information -> PROCESS -> Knowledge -> PROCESS -> Wisdom

### Purpose of Database Systems
1) Data redundancy and inconsistency
        Multiple file formats, duplication of information in different files
2) Difficulty in accessing data
        Need to write a new program to carry out each new task
3) Data isolation
        multiple files and formats
4) Integrity problems
        Integrity constraints (e.g. account balance > 0) become part of program code
        Hard to add new constraints or change existing ones
        Drawbacks of using file systems
5) Atomicity of updates
        E.g. transfer of funds from one account to another should either complete or not happen at all
6) Concurrent access by multiple users
7) Security problems
   
### Database Technologies
1) Schema
        Logical schema
        Physical schema
2) Instance
```
alter table comments
add foreign key (post_id) references posts(id)
```
```
alter table comments
drop foreign key comments_iblk_1
```

```
alter table comments
add foreign key (post_id) references posts(id) on delete cascade on update
```
### Types of joins
<ul>
    <li>INNER JOIN: Only matching rows.
    <li>LEFT JOIN: All rows from the left table, and matching rows from the right table.</li>
    <li>RIGHT JOIN: All rows from the right table, and matching rows from the left table.</li>
    <li>FULL OUTER JOIN: All rows from both tables, with NULLs where there is no match.</li>
    <li>CROSS JOIN: Cartesian product of both tables.</li>
    <li>SELF JOIN: Table joined with itself.</li></li>
</ul>

### Group Results With Aggregate Functions
```
select
    customer.customer_id, customer.first_name, customer.last_name, count(rental.rental_id) rentals_checked_out
from customer
left join rental
on rental.customer_id = customer.customer_id
group by customer.customer_id
```
```
select
    customer.customer_id, customer.first_name, customer.last_name, rental.rental_id
from customer
left join rental
on rental.customer_id = customer.customer_id
group by customer.customer_id, rental_id
```