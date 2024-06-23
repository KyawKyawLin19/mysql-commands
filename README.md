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