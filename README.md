# SQL-SCRIPTS
THIS REPOSITORY CONTAINS SQL SCRIPT DATA AND DAS


**SCRIPT 1**
create table personal_info(
personal_id  INT primary key not null,
name text,
country text,
tribe text,
age INT,
room_no INT,
shoe_size INT,
family_members INT
);

create table profession_info(
professional_id INT primary key  not null,
salary INT,
linkedin_followers INT,
table_no INT,
personal_id INT,
foreign key (personal_id) references personal_info(personal_id)
);

create table health_info(
health-id INT primary key  not null,
height FLOAT,
mestrual_cycle INT,
personal_id INT,
foreign key (personal_id) references personal_info(personal_id)
);

create table preference_info(
preference_id INT primary key  not null,
favourite_food text,
favourite_book VARCHAR(2),
color text,
personal_id INT,
foreign key (personal_id) references personal_info(personal_id)
);

insert into personal_info(personal_id, name, country, tribe, age, room_no, shoe_size, family_members)
values
(1, 'MaryVivian Muthoni', 'Kenya', 'Kikuyu', 25, 101, 9, 4),
((2, 'Hawa Majid', 'Tanzania', 'Swahili', 30, 202, 7, 3),
(3, 'Faith Wanjiru', 'Kenya', 'Kikuyu', 22, 203, 8, 2);


insert into profession_info(profession_id, salary, linkedin_followers, table_no, personal_id)
values
(1, 80000, 500, 1, 1),
(2, 90000, 600, 2, 2),
(3, 70000, 400, 3, 3);

insert into health_info(health_id, height, menstrual_cycle, personal_id)
values
(1, 180.5, 28, 1),
(2, 170.0, 30, 2),
(3, 175.0, 32, 3);

insert into preference_info(preference_id, favourite_food, favourite_book, color, personal_id)
values
(1, 'Pizza', 1984, 'Blue', 1),
(2, 'Burger', 'To Kill a , Mockingbird', 'Red', 2),
(3, 'Salad', 'Harry Potter', 'Green', 3);

select favourite_food, color
from preference_info;

select * from health_info;

select personal_info.personal_id = health_info.personal_id;
from personal_info
left join health_info on personal_info.personal_id = health_info.personal_id;

select personal_info.personal_id = health_info.personal_id;
from personal_info
left join health_info on personal_info.personal_id = health_info.personal_id;

select personal_info.personal_id = health_info.personal_id;
from personal_info
left join health_info on personal_info.personal_id = health_info.personal_id
union all 
select personal_info.personal_id = health_info.personal_id
from personal_id
right join health_info on personal_info.personal__id = health_info.personal_id;




**SCRIPT 2**

CREATE TABLE student_info(
    student_id INT PRIMARY KEY  NOT NULL,
    name TEXT,
    country TEXT,
    tribe TEXT,
    age INT CHECK (age >= 18),
    room_no INT,
    shoe_size INT,
    family_members TEXT
);
INSERT INTO student_info(student_id, name, country, tribe, age, room_no, shoe_size, family_members)
VALUES
    (1, 'Mary Vivian Muthoni', 'Kenya', 'Kikuyu', 25, 101, 9, '4'),
    (2, 'Hawa Majid', 'Tanzania', 'Swahili', 30, 202, 7, '3'),
    (3, 'Faith Wanjiru', 'Kenya', 'Kikuyu', 22, 203, 8, '2');
   
   select * from student_info;
  
CREATE TABLE profesion_info(
    profesion_id INT PRIMARY KEY  NOT NULL UNIQUE,
    salary INT,
    linkedln_followers INT,
    table_no INT,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES student_info(student_id)
);
INSERT INTO profesion_info(profesion_id, salary, linkedln_followers, table_no, student_id)
VALUES
    (1, 80000, 500, 1, 1),
    (2, 90000, 600, 2, 2),
    (3, 70000, 400, 3, 3);
select * from profesion_info;
CREATE TABLE health_info(
    health_id INT PRIMARY KEY NOT NULL,
    height FLOAT,
    menstrual_cycle INT,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES student_info(student_id)
);
INSERT INTO health_info(health_id, height, menstrual_cycle, student_id)
VALUES
    (1, 180.5, 28, 1),
    (2, 170.0, 30, 2),
    (3, 175.0, 32, 3);
CREATE TABLE preferenced_info(
   preference_id INT primary key not null,
    favourite_food TEXT,
    favourite_book TEXT,
    color TEXT,
    name text,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES student_info(student_id)
);
INSERT INTO preferenced_info(preference_id, favourite_food, favourite_book, color, name, student_id)
VALUES
    (1, 'Pizza', 'Saveme', 'Mary',  'Blue', 1),
    (2, 'Burger', 'Mocking', 'Vivian', 'Red', 2),
    (3, 'Salad', 'Harry Potter',  'Muthoni', 'Green', 3);
INSERT INTO profesion_info(profesion_id, salary, linkedln_followers, table_no, personal_id)
VALUES
    (1, 80000, 500, 1, 1),
    (2, 90000, 600, 2, 2),
    (3, 70000, 400, 3, 3);
SELECT favourite_food, color
FROM preference_info;
SELECT * FROM health_info;
SELECT student_info.student_id, health_info.menstrual_cycle
FROM student_info
LEFT JOIN health_info ON student_info.student_id = health_info.student_id;
SELECT student_info.student_id,preference_info.favourite_food
FROM student_info
LEFT JOIN preference_info  ON student_info.student_id = preference_info.student_id;
select name
from student_info
union
select favourite_book
from preference_info;
select student_info.tribe,student_info.country, profesion_info.salary,profesion_info.linkedln_followers
from student_info
RIGHT join profesion_info on student_info.student_id=profesion_info.student_id;
select student_info.shoe_size,student_info.country, profesion_info.salary,profesion_info.linkedln_followers
from student_info
LEFT join profesion_info on student_info.student_id=profesion_info.student_id;



