# SQL

<!-- SECTION Commands -->
  CREATE TABLE table_name(column ATTRIBUTES, etc.) --> Creates table
  DROP TABLE table_name --> Deletes table
  INSERT INTO --> Adds row to table
    table_name ( column, etc. ) --> States order of values
    VALUES ( 'value', etc. ) --> Gives values (can do multiple times)
  SELECT column, column FROM table_name --> Returns all values from given columns or * to return table
    WHERE conditional --> Returns row where conditional is true
    LIMIT 2 OFFSET 1 --> Gets only specified amount offset by amount
  UPDATE table_name SET --> Changes value of said column where conditional is true
    column = value
    WHERE conditional
    LIMIT 2 OFFSET 1
  DELETE FROM table_name --> Deletes row where conditional is true
    WHERE conditional
    LIMIT 2 OFFSET 1
  ALTER TABLE table_name
    ADD column ATTRIBUTES --> Adds new column to table
  SELECT LAST_INSERT_COLUMN(); Gets the last create row's value from said column

<!-- SECTION Data types -->
  VARCHAR(INT) --> Int determines the length of string
  INT --> Number (Can change prefix to dictate byte size)
    UNSIGNED --> Only positive numbers
  DECIMAL --> Number with decimals
  BOOLEAN --> True and False
  DATE --> Just date (YYYY-MM-DD)
  DATETIME --> Date and Time

<!-- SECTION Attributes -->
  NOT NULL --> Value cannot be null (required)
  PRIMARY KEY --> Has to be unique
  DEFAULT --> Following statement is the default value
  CURRENT_TIMESTAMP --> Makes value the current time
  ON UPDATE --> When table is edited updates value with following statement
  AUTO_INCREMENT --> Increments value with each new value
  COMMENT --> Description for dev
  default charset utf8; --> Ends table and sets default font