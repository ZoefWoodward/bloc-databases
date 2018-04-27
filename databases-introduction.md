#### Exercises

>1. What data types do each of these values represent?
```
1. "A Clockwork Orange"
`A: String`
2. 42
`A: Integer`
3. 09/02/1945
`A: Date`
4. 98.7
`A: Float`
5. $15.99
`A: Float`
```

>2. Explain when a database would be used. Explain when a text file would be used.
`A: A text file might be more suitable for JSON data, whereas a database would be used to quickly store and change large amounts of data.`

>3. Describe one different between SQL and other programming languages.
`A: SQL is a declarative language rather than a procedural language.`

>4. In your own words, explain how the pieces of a database system fit together at a high level.
`A: So the database is laid out like a table, with rows and columns, each containing a value corresponding to it's data type, but is unreadable to humans, and has the ability to query and manipulate data.`

>5. Explain the meaning of table, row, column, and value.
`A: A table contains rows and columns, the columns reach from top to bottom, and the rows reach from left to right, all of the values are divided into cells and assigned to a particular type of data.`

>6. List three data types that can be used in a table.
`A: Integer, Float, String.`

>7. Given this payment table, provide an English description of the following queries and include their results:
```SELECT date, amount
     FROM payments;

     SELECT amount
     FROM payments
     WHERE amount > 500;

     SELECT *
     FROM payments
     WHERE payee = 'Mega Foods';
```
`A: This query will return all payment amounts under 500 from Mega Foods.`

>8. Given this users table, write SQL queries using the following criteria and include the output.

The email and sign-up date for the user named DeAndre Data.
```
SELECT email, signup
FROM users
WHERE name = 'DeAndre Data'

```
The user ID for the user with email 'aleesia.algorithm@uw.edu'.
```
SELECT userid
FROM users
WHERE email = 'aleesia.algorithm@uw.edu'
```
All the columns for the user ID equal to 4.
```
SELECT *
FROM users
WHERE userid = '4'
```
