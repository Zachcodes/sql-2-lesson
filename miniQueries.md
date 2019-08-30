<!-- Create table movie -->
create table movie (
    movie_id serial primary key,
    title text,
    media_type_id integer references media_type(media_type_id)
)

<!-- Insert new movie -->
insert into movie (title, media_type_id)
values ('Saving Private Ryan', 2);

<!-- Select new movie -->
select * from movie;

<!-- Add column to genre_id -->
alter table movie
add column genre_id integer references genre(genre_id)

<!-- Select movie -->
select * from movie;

<!-- Update movie -->
update movie
set genre_id = 22
where movie_id = 1

<!-- Join artist and album -->
select * from artist ar
join album al
on al.artist_id = ar.artist_id

<!-- sub select -->
select * from track
where genre_id in (select genre_id from genre where name in ('Jazz','Blues'))

<!-- Setting to null and running query -->
select * from customer
where company is null;

<!-- count and group -->
select count(*), ar.artist_id, ar.name from artist ar
join album al on al.artist_id = ar.artist_id
group by ar.artist_id;

select count(*), ar.artist_id, ar.name from artist ar
join album al on al.artist_id = ar.artist_id
group by ar.artist_id
order by count(*) desc;

<!-- select distinct -->
select distinct country from customer;

<!-- delete from -->
delete from customer
where fax is null;
