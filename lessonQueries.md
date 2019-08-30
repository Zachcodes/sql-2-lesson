# Sql order of operations

1. from - Choose and join tables to get base data
2. where - filters the base data
3. group by - aggregates the base data 
4. having - filters the aggregated data
5. select - returns the final data 
6. order by - sorts the final data 
7. limit - limits the returned data to a row count

# Altering a table 

<!-- Altering a table -->
create table pets (
    id serial primary key,
    type text
)

<!-- adding a column -->
ALTER TABLE pets
ADD COLUMN name text

<!-- altering column data type -->
ALTER TABLE pets
ALTER COLUMN type
SET DATA TYPE varchar(20);

ALTER TABLE pets
ALTER type
TYPE varchar(20);

<!-- renaming a column -->
ALTER TABLE pets
RENAME COLUMN type
TO species;

<!-- Dropping a column -->
ALTER TABLE pets
DROP COLUMN name;

<!-- renaming a table -->
ALTER TABLE pets
RENAME TO animals;

<!-- Dropping a table -->
DROP TABLE animals

<!-- STOP HERE - MOVE IN TO RELATIONSHIPS -->

# Sub select

<!-- nested subquery -->
select * from album
where artist_id in (
  	select artist_id from artist 
  where name ilike 'a%'
  );

# Group by

<!-- group by -->
select count(*), composer
from track
group by composer;

<!-- select count(*), composer
from track
where composer ilike 'a%'
group by composer
having count(*) > 10; -->

# Having 

<!-- having -->
select count(*), composer
from track
group by composer
having count(*) > 10;

<!-- select count(*), composer
from track
group by composer
having count(*) > 10
and composer is not null; -->