# Review (Start of class)

<!-- Basic Select -->
select * from album;

<!-- Basic select with columns -->
select artist_id, title 
from album;

<!-- Select with where clause -->
select * from album
where artist_id = 1;

<!-- Select distinct -->
select distinct country from customer;

<!-- Comparison operators  -->
select * from invoice 
where total > 10;

select * from invoice 
where customer_id != 5;

<!-- selecting from list of values (in) -->
select * from invoice 
where customer_id in (2, 4, 5);

select * from invoice 
where customer_id not in (2, 4, 5);

<!-- partial matching -->
select * from album 
where title like 'A%'

select * from album 
where title ilike 'a%'

<!-- Multiple where clauses -->
select * from album 
where title ilike 'a%'
and artist_id = 18

<!-- ordering results -->
select * from invoice
order by total desc;

select * from invoice
order by total asc;

<!-- aggregate functions -->
select max(total) from invoice;

select min(total) from invoice;

select avg(total) from invoice;

select sum(total) from invoice;

<!-- count records -->
select count(*) from invoice
where total > 10;

<!-- limit records set -->
select * from invoice
limit 20;

<!-- query for null values -->
select * from customer
where state is null

select * from customer
where state is not null

<!-- creating a new table -->
create table vacation_spots (
    id serial primary key,
    location text
)

<!-- inserting new rows -->
insert into vacation_spots (location)
values ('Denmark'), ('Italy');

select * from vacation_spots;

<!-- Delete from -->
select * from vacation_spots
where id = 1;

delete from vacation_spots
where id = 1;

<!-- Update -->
select * from vacation_spots
where id = 2;

update vacation_spots
set location = 'China'
where id = 2;

select * from vacation_spots;