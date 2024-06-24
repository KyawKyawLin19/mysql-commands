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

### SQL (Structured Query Language)
1) DDL (Data Definition Language)- create, drop, alter, truncate
2) DML (Data Manipulation Language) - insert, update, delete
3) DCL (Data Control Language) - grant, revoke
4) TCL (Transaction Control Language) - commit, rollback, savePoint
5) DQL (Data Query Language) - select

### Role and duties of DBA
1) Coordinates all the activities of the database system
2) The database administrator has a good understanding of the enterprise's information resources and needs.
3) Schema definition (database structure, table structure, data models, data relationships)
4) Storage Structure and access method definition
5) Schema and physical organization modification
6) Granting user authroity to access the database
7) Specifying integrity constraints
8) Acting plans for the users
9) Monitoring performance and responding to changes in requirements
10) And more.
   
### Database Technologies
1) Schema
        Logical schema
        Physical schema
2) Instance

### Advantages of Database
1) Storage Management
2) Transaction Management
3) Security Management

### Data Models
- A collection of tools for describing
  . data
  . data relationships
  . data semantics
  . data constraints
- Entity Relationship Model(ER)
- Relational model
- Other models:
  . object-oriented model
  . semi-structured data models
  . Older models : network model and hierarchical model

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