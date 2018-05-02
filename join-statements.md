#### Exercises

>1. How do you find related data held in two separate data tables?
`A: To find related data held in two separate data tables, you would use an INNER JOIN statement.`

>2. Explain, in your own words, the difference between an INNER JOIN, LEFT OUTER JOIN, and RIGHT OUTER JOIN. Give a real-world example for each.
```
INNER JOIN: This will return data values with matching rows from each table. For example, we want a list of athlete names and ages from a list of athletes that are involved in more than one athletic department. So we would join the tables and return the names and which departments they are in.

LEFT OUTER JOIN: This will return the records listed in the left table, and only return the matching records listed in the right table.
For example, A table of fruit types, and apples will be null if none have been purchased and added to the table.

RIGHT OUTER JOIN: This will return the records listed in the right table, and only return the matching records listed in the left table.
For example, A table of all of the purchased fruit, and the apples section will be null because none were purchased.
```

>3. Define primary key and foreign key. Give a real-world example.
```
Primary Key: This is a unique identifier for each row in a database table.
For example, In an Employee table, you can choose either Employee ID or SNN column for a primary key. EmployeeID is preferable choice because SSN is a secure (PII) value.
Foreign Key: This is the primary key of one table that is included as a non-unique attribute in another table. Foreign key sets up a relationship between two tables, the other key should have a referencing key as a primary key. Like an employee table you can reference Department ID with Department table's Department ID primary key.
```

>4. Define aliasing
`A: Aliasing is a technique of creating short variable names, usually a single letter (d for department) to replace the table name in a query.`

>5. Change this query so that you are using aliasing:
SELECT professor.name, compensation.salary,
compensation.vacation_days FROM professor JOIN
compensation ON professor.id =
compensation.professor_id;
```
SELECT p.name, c.salary, c.vacation_days
FROM professor AS p
JOIN compensation AS c
ON p.id = c.professor_id;
```

>6. Why would you use a NATURAL JOIN? Give a real world example.
`A: A NATURAL JOIN will join tables using all the common columns between them. For example, Returning a table with fruit types and all purchased fruits.`

>7. Using this Employee schema and data, write queries to find the following information:
List all employees and all shifts.
```
SELECT employees.name, scheduled_shifts.shift_id
FROM employees
JOIN scheduled_shifts
ON employees.id = scheduled_shifts.employee_id;
```

>8. Using this Adoption schema and data, please write queries to retrieve the following information and include the results:
-Create a list of all volunteers. If the volunteer is fostering a dog, include each dog as well.
-The cat's name, adopter's name, and adopted date for each cat adopted within the past month to be displayed as part of the "Happy Tail" social media promotion which posts recent successful adoptions.
-Create a list of adopters who have not yet chosen a dog to adopt.
-Lists of all cats and all dogs who have not been adopted.
-The name of the person who adopted Rosco.
```
-SELECT volunteers.first_name, dogs.name AS dog_name
FROM volunteers
LEFT OUTER JOIN dogs
ON volunteers.foster_dog_id = dogs.id;

Results:
first_name	dog_name
Rubeus	Munchkin
Marjorie	Marmaduke
Sirius	(null)
Remus	(null)
Albus	(null)

-SELECT cats.name AS cat_name, adopters.first_name AS adopter_name, cat_adoptions.date AS adoption_date
FROM cats
JOIN cat_adoptions ON cats.id = cat_adoptions.cat_id
JOIN adopters ON cat_adoptions.adopter_id = adopters.id
WHERE cat_adoptions.date >= (CURRENT_DATE - INTERVAL '30 DAYS');

Results:
cat_name	adopter_name	adoption_date
Mushi	Arabella	2018-04-12
Victoire	Argus

-SELECT adopters.first_name
FROM adopters
LEFT OUTER JOIN dog_adoptions
ON adopters.id = dog_adoptions.adopter_id
WHERE dog_adoptions.adopter_id IS NULL;

Results:
first_name
Hermione
Arabella

-SELECT dogs.name
FROM dogs
LEFT OUTER JOIN dog_adoptions
ON dogs.id = dog_adoptions.dog_id
WHERE dog_adoptions.dog_id IS NULL

UNION ALL

SELECT cats.name
FROM cats
LEFT OUTER JOIN cat_adoptions
ON cats.id = cat_adoptions.cat_id
WHERE cat_adoptions.cat_id IS NULL;

Results:
name
Boujee
Munchkin
Marley
Lassie
Marmaduke
Seashell
Nala

-SELECT adopters.first_name, adopters.last_name
FROM adopters
JOIN dog_adoptions
ON adopters.id = dog_adoptions.adopter_id
WHERE dog_adoptions.dog_id = 10007;

Results:
first_name	last_name
Argus	Filch
```

>9. Using this Library schema and data, write queries applying the following scenarios and include the results:
-To determine if the library should buy more copies of a given book, please provide the names and position, in order, of all of the patrons with a hold (request for a book with all copies checked out) on "Advanced Potion-Making".
-List all of the library patrons. If they have one or more books checked out, list the books with the patrons.

-SELECT patrons.name, holds.rank
FROM patrons
JOIN holds
ON patrons.id = holds.patron_id
WHERE isbn = '9136884926';

Results:
name	rank
Terry Boot	1
Cedric Diggory	2

-SELECT DISTINCT patrons.name,
(SELECT checkedout.title AS "books checked out"
 FROM
   (SELECT transactions.patron_id, transactions.checked_in_date, books.title
    FROM transactions LEFT OUTER JOIN books ON books.isbn = transactions.isbn
    WHERE transactions.checked_in_date IS NULL) AS checkedout
  WHERE checkedout.patron_id = patrons.id)
 FROM patrons
 LEFT OUTER JOIN transactions ON transactions.patron_id = patrons.id
 LEFT OUTER JOIN books on books.isbn = transactions.isbn;

Results:
name	books checked out
Cedric Diggory	Fantastic Beasts and Where to Find Them
Cho Chang	(null)
Hermione Granger	(null)
Padma Patil	(null)
Terry Boot	Advanced Potion-Making
