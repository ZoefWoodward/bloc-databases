####Exercises

>1. List the commands for adding, updating, and deleting data.
`Adding: INSERT INTO`
`Updating: UPDATE`
`Deleting: DELETE`

>2. Explain the structure for each type of command.
```
INSET INTO: This inserts data into the table.
INSERT INTO (table name) (column names);

UPDATE: This modifies existing records within a table.
UPDATE (table name) SET (column name) = (new value) WHERE (column name) = (value);

DELETE: This deletes an entry from a table. (Irreversible)
DELETE FROM (table name) WHERE (table column) = (value);
```
>3. What are some of the data types that can be used in tables? Give a real-world example of each type.
`A: Movie Showings Table. For example, Date, Timestamp, Integer for price, String for name, etc.`

>4. Decide how to create a new table to hold a list of people invited to a wedding dinner. The table needs to have first and last names, whether they sent in their RSVP, the number of guests they are bringing, and the number of meals (1 for adults and 1/2 for children).
Which data type would you use to store each of the following pieces of information?
First and last name.
Whether they sent in their RSVP.
Number of guests.
Number of meals.
Write a command that creates the table to track the wedding dinner.
Write a command that adds a column to track whether the guest sent a thank you card.
You have decided to move the data about the meals to another table, so write a command to remove the column storing the number meals from the wedding table.
The guests will need a place to sit at the reception, so write a command that adds a column for table number.
The wedding is over and we do not need to keep this information, so write a command that deletes the table numbers from the database.
```
CREATE TABLE guests (
  first name string,
  last name string,
  RSVP'd boolean,
  added guests integer,
  meals integer;
  );

-ALTER TABLE guests ADD COLUMN thank you boolean;
-ALTER TABLE guests DROP COLUMN meals
-ALTER TABLE guests ADD COLUMN table number integer;
-ALTER TABLE guests DROP COLUMN table number;
```

>5. Write a command to create a new table to hold the books in a library with the columns ISBN, title, author, genre, publishing date, number of copies, and available copies.
Find three books and add their information to the table.
Someone has just checked out one of the books. Change the number of available copies to 1 fewer.
Now one of the books has been added to the banned books list. Remove it from the table.
```
CREATE TABLE library books (
ISBN varchar,
title string,
author string,
genre string,
publishing date date,
copies integer,
available copies integer
);

INSERT INTO library books
VALUES

(B015X5KBJG, 'Milk and Honey', 'Rupi Kaur', 'Women's Poetry', October 6 2015, 16, 3),

(9781594634727, 'Big Magic', 'Elizabeth Gilbert', 'Self Help', September 27 2016, 42, 31),

(9780735224292, 'Little Fires Everywhere', 'Celeste Ng', 'Fiction', September 12 2017, 4, 1);

UPDATE library books SET available copies = 0 WHERE ISBN = 9780735224292;

DELETE FROM library books WHERE ISBN = 9780735224292;
```

>6. Write a command to make a new table to hold spacecrafts. Information should include id, name, year launched, country of origin, a brief description of the mission, orbiting body, if it is currently operating, and its approximate miles from Earth. In addition to the table creation, provide commands that perform the following operations:
Add three non-Earth-orbiting satellites to the table.
Remove one of the satellites from the table since it has just crashed into the planet.
Edit another satellite because it is no longer operating and change the value to reflect that.
```
CREATE TABLE spacecrafts (
  id varchar,
  name string,
  year launched date,
  country of origin string,
  mission brief text,
  orbiting body string,
  currently operating boolean,
  approx. miles from earth numeric
  );

INSERT INTO spacecrafts
VALUES
('1994-004A', 'Clementine', January 25 1994, 'USA', '80-minute lunar mapping phase', 'Lunar Orbiter', FALSE, 3,178.9),

('1959-014A', 'Luna 2', September 12 1959, 'Russia', 'Path set to moon', 'Lunar Impactor', FALSE, 3000),

('2011-040A', 'Juno', August 5 2011, 'USA', 'uno's mission is to measure Jupiter's composition, gravity field, magnetic field, and polar magnetosphere', 'Jupiter Orbiter', TRUE, 347);

DELETE FROM spacecrafts WHERE id = '1959-014A';
UPDATE spacecrafts SET currently operating = FALSE WHERE id = '2011-040A';
```

>7. Write a command to create a new table to hold the emails in your inbox. This table should include an id, the subject line, the sender, any additional recipients, the body of the email, the timestamp, whether or not you have read the email, and the id of the email chain it's in. Also provide commands that perform the following operations:
-Add three new emails to the inbox.
-You deleted one of the emails, so write a command to remove the row from the inbox table.
-You started reading an email but just heard a crash in another room. Mark the email as unread before investigating the crash, so you can come back and read it later.
```
CREATE TABLE inbox (
  id varchar,
  subject 'string',
  sender 'string',
  CC 'string',
  body text,
  time timestamp ,
  read boolean,
  chain id varchar
  );

  INSERT INTO inbox
  VALUES
  (03, 'Following up', 'Jane Fonda', 'Russel Crowe', 'What do you think about the movie idea we talked about?', 2018-04-30 03:30:00, TRUE, 00333 )

  (02, 'Sorry for your loss', 'John Doe', 'Jane Doe', 'Sorry about the loss of your cat.', 2018-04-29 02:00:00, FALSE, 00332)

  (01, 'Shocking News', 'Luke Skywalker', 'None', 'HE IS MY FATHER.', 1980-05-21 01:30:00, TRUE, 00331);

  DELETE FROM inbox WHERE id = 03;
  UPDATE inbox SET read = FALSE WHERE id = 01;
```
