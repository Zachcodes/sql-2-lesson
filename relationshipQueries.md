<!-- One to one relationships -->
A person will only have one social security number
a person will only have one login


<!-- One to many relationships -->
A book can have many authors 
A class can have only one teacher but a teacher can teach multiple classes

<!-- many to many relationships -->
A student may take multiple classes and a class may have multiple students (junction table)

# Creating tables with Foreign keys

<!-- foreign keys -->
CREATE TABLE networth (
  id SERIAL PRIMARY KEY,
  foreign_id INTEGER REFERENCES artist (artist_id),
  amount integer
)

<!-- adding foreign key after creation -->
ALTER TABLE networth
ADD COLUMN artist_id integer REFERENCES artist (artist_id)

# Joining Tables (point out aliasing)

<!-- Inner join (gives you the union of both tables) -->
select *
from artist ar
join album al
on al.artist_id = ar.artist_id;

<!-- outer join (gives you union of both as well as rows from both that dont have a match) -->
select *
from artist ar
full join album al
on al.artist_id = ar.artist_id;

<!-- Left join (joins records and pulls all from left table regardless of match) -->
select *
from artist ar
left join album al
on al.artist_id = ar.artist_id;

<!-- Right join (joins records and pulls all from left table regardless of match) -->
select *
from artist ar
right join album al
on al.artist_id = ar.artist_id;

# Relationship examples

<!-- one to one relationship set up  -->
create table social_security_number (
    id serial primary key,
    number integer 
);

create table person (
    id serial primary key,
    name text,
    social_security_id integer references social_security_number(id) UNIQUE
);

insert into social_security_number (number) 
values (22342432);

insert into person (name, social_security_id)
values ('Zach', 1);

insert into person (name, social_security_id) 
values ('John', 1);

<!-- one to many relationship set up -->
create table class (
    id serial primary key,
    class_name text,
    teacher_id integer references teacher(id)
);

create table teacher (
    id serial primary key,
    teacher_name text
);

insert into teacher(teacher_name)
values ('James');

insert into class (class_name, teacher_id)
values ('Biology', 1), ('Chemistry', 1);


<!-- Many to many relationship set up -->
create table classes (
    id serial primary key,
    class_name text
);

create table students (
    id serial primary key,
    student_name text
);

create table class_student_link (
    id serial primary key,
    student_id integer references students(id),
    class_id integer references classes(id)
);

insert into classes (class_name) 
values ('Biology'), ('Chemistry');

insert into students (student_name)
values ('John'), ('Lisa');

insert into class_student_link (student_id, class_id)
values (1, 1), (1, 2), (2, 1), (2, 2);

select * from 
classes c
join class_student_link l
on l.class_id = c.id 
join students s 
on l.student_id = s.id;