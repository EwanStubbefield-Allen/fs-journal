# CSharp and SQL Fundamentals
01. What is the purpose of a `namespace`?

  > Namespace allows files to communicate to each other.

02. What is the difference between a `class` and an `interface`?

  > An interface can only have declarations whereas a class can have both declarations and definitions.

03. What is the method that returns an instance of a class, yet it has no return type?

  > The constructor

05. In the Car example what is the access modifier of the `Start()` method?

  ```c#
  abstract class Car
  {
    public string Start()
    {

      return "Vroooom";

    }
  }
  ```

  > The access modifier of Start() is public.

06. In the Car example what is `string` an indication of?

  > string indicates what data type the function will return.

07. In the Car example what is `abstract` preventing?

  > abstract prevents creating an instance of that class.

08. In a SQL table, what is the difference between information in a row and information in a column?

  > Columns are specified properties, whereas rows are complete objects.

09. Demonstrate the necessary SQL for creating a table called `characters` with the values `name, age, description` as strings, and an `int` id.

  > CREATE TABLE
    characters(
      id int NOT NULL PRIMARY KEY,
      name VARCHAR(255) NOT NULL,
      age VARCHAR(255) NOT NULL,
      description VARCHAR(255) NOT NULL
    ) default charset utf8 COMMENT '';

10. In SQL how can you query more than a single table? Provide an example.

  > Make a list of tables using commas.
    SELECT * FROM group1, group2