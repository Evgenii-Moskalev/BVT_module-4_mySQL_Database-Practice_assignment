CREATE DATABASE bvt_demo_2;
USE bvt_demo_2;

CREATE TABLE school (
id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(255),
date_founded DATE,
date_entered DATETIME
);
CREATE TABLE student (
id INT NOT NULL AUTO_INCREMENT,
first_name VARCHAR(255),
last_name VARCHAR(255),
school_id INT NOT NULL,
start_date DATE,
data_entered DATETIME,

PRIMARY KEY (id),
FOREIGN KEY (school_id) REFERENCES school(id)
);

INSERT INTO school (name, date_founded, date_entered)
VALUES ('Coding Academy', '2019-01-01', NOW()), 
	('Digital Skills', '2020-02-02', NOW()),
    ('Marketing Skills', '2021-03-03', NOW());
    
INSERT INTO student (first_name, last_name, school_id, start_date, data_entered)
VALUES ('Leonardo', 'DiCaprio', 3, '2022-06-21', '2022-06-22'),
	('Johnny', 'Depp', 1, '2019-01-10', '2019-01-10'),
    ('Tom', 'Cruise', 1, '2020-08-01', '2020-07-27'),
    ('Mr.', 'Smith', 2, NOW(), NOW()),
    ('Mrs.', 'Smith', 2, NOW(), NOW());
    
SELECT * FROM student 
WHERE school_id != 1 
-- ORDER BY start_date 
LIMIT 1;

SELECT * FROM school 
ORDER BY date_founded 
-- DESC
;

SELECT student.first_name AS 'Student Name', 
	student.last_name AS 'Student Last Name', 
    school.name AS 'School Name',
    student.start_date AS Since
FROM student
LEFT JOIN school ON student.school_id = school.id;

UPDATE student
SET school_id = 1
WHERE last_name = 'Smith';

DELETE FROM student
WHERE school_id != 1;

SELECT * FROM student
LEFT JOIN school ON student.school_id = school.id
ORDER BY student.start_date 
DESC;


DROP TABLE school;
DROP TABLE student;