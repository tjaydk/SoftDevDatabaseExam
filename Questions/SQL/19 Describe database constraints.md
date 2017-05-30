## 19 Describe database constraints

Constraints in a SQL database are used to specify rules for data in a table. This is used to limit the type of data that can go into a table. By doing this the accuracy and reliability of data in tables are ensured. Constraint can be either on a column level or an entire table.

Adding constraints can be done when a table is created, or with the ALTER TABLE command. The following is an example of creating a table with constraints:

````mysql
CREATE TABLE Books (
	UID BIGINT PRIMARY KEY,
	Title VARCHAR(255) NOT NULL,
	Text VARCHAR(255) NOT NULL
);
````

If we were to do the same with the ALTER TABLE command it would look like this:

````mysql
CREATE TABLE Books (
	UID BIGINT,
	Title VARCHAR(255),
	Text VARCHAR(255)
);
ALTER TABLE Books ADD PRIMARY KEY(UID);
ALTER TABLE Books MODIFY Title VARCHAR(255) NOT NULL;
ALTER TABLE Books MODIFY Text VARCHAR(255) NOT NULL;
````

If we then try to make an insert statement like

````mysql
insert into books(UID, Title, Text) VALUES (1, null, 'Some Text');
````

it will return an error as title cant be null.

### Common Constraints

- NOT NULL: The NOT NULL constraint ensures that a column cant have null values as its data.
- UNIQUE: The UNIQUE constraint ensures that all values in a column are different.
- PRIMARY KEY: A combination of the NOT NULL and UNIQUE constraint. 
- FOREIGN  KEY: Identifies a UNIQUE row in another table.
- CHECK: Ensures that all values in a column satisfies a condition.
- DEFAULT: Sets a default value to a column when no value is added.
- INDEX: Used to create and retrieve data from the database faster.