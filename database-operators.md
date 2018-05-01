#### Exercises

>1. Write out a generic SELECT statement.
```
SELECT *
FROM candy
WHERE flavor = mint;
```
>2. Create a fun way to remember the order of operations in a SELECT statement, such as a mnemonic.
```
S-F-J-W-G-H-O-L
SELECT-FROM-JOIN-WHERE-GROUP-HAVING-ORDER-LIMIT
"Sharks fight jellyfish with guns! Hide on land!"
```

>3. Given this dogs table, write queries to select the following pieces of data:
Intake teams typically guess the breed of shelter dogs, so the breed column may have multiple words (for example, "Labrador Collie mix").
-Display the name, gender, and age of all dogs that are part Labrador.
-Display the ids of all dogs that are under 1 year old.
-Display the name and age of all dogs that are female and over 35lbs.
-Display all of the information about all dogs that are not Shepherd mixes.
-Display the id, age, weight, and breed of all dogs that are either over 60lbs or Great Danes.
```
SELECT "name", "gender", "age"
FROM dogs
WHERE breed LIKE '%labrador%'

SELECT id
FROM dogs
WHERE age < 1

SELECT name, age
FROM dogs
WHERE gender = 'F' AND weight > 35

SELECT *
FROM dogs
WHERE breed NOT LIKE '%shepherd%'

SELECT id, age, weight, breed
FROM dogs
WHERE weight > 60 OR breed = 'great dane'
```

>4. Given this cats table, what records are returned from these queries?
SELECT name, adoption_date FROM cats;
SELECT name, age FROM cats;
```
name	adoption_date
Mushi	2016-03-22
Seashell	(null)
Azul	2016-04-17
Victoire	2016-09-01
Nala	(null)


name	age
Mushi	1
Seashell	7
Azul	3
Victoire	7
Nala	1
```

>5.From the cats table, write queries to select the following pieces of data.
Display all the information about all of the available cats.
Choose one cat of each age to show to potential adopters.
Find all of the names of the cats, so you don’t choose duplicate names for new cats.
```
SELECT *
FROM cats;

SELECT DISTINCT age
FROM cats;

SELECT DISTINCT name
FROM cats;
```

>6. List each comparison operator and explain when you would use it. Include a real world example for each.
```
= equal : An apple is equal to the apples id.
!= not equal : An apple is not equal to an orange.
>= greater than or equal to : The apple is greater than or equal to the weight of another apple in the bunch.
<= less than or equal to : The apple is less than or equal to the weight of another apple in the bunch.
> greater than : A watermelon's weight, is greater than an apple's weight.
< less than : A kiwi's weight is less than an apple's weight.
<> greater than or less than : Finding whether we have fruit in the basket where the weight is greater than or less than an apple.
```

>7. From the cats table, what data is returned from these queries?
SELECT name FROM cats WHERE gender = ‘F’;
SELECT name FROM cats WHERE age <> 3;
SELECT ID FROM cats WHERE name != ‘Mushi’ AND gender = ‘M’;
```
name
Seashell
Nala

name
Mushi
Seashell
Victoire
Nala

id
3
4
```
