# A bit more CSharp and SQL
1. What does ***inheritance*** accomplish for us in C#?

  > Inheritance allows to reuse code for other aspects

2. How does ***member inheritance*** work in C#? Does a `Class` inherit all members of the base `Class`?

  > A class does not inherit the constructor and finalizers from the base class

3. How does ***accessibility*** affect inheritance?

  > Accessibility determines which member is inherited by the derived class.

4. What is the difference between a `PRIMARY KEY` and a `FOREIGN KEY`

  > A primary key is unique for that row in the table whereas a foreign key references a primary key from another table.

5. What is an ***alias***?

  > An alias is a temporary name given to a table that the current command can use to reference the table.

6. Demonstrate how you would query a join statement that would get all of a doctors patients from the following collections:

  ```SQL
  CREATE TABLE doctors (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patients (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patient_doctors (
    id INT NOT NULL AUTO_INCREMENT,
    doctorId INT NOT NULL,
    patientId INT NOT NULL,

    FOREIGN KEY (doctorId)
      REFERENCES doctors(id),
    FOREIGN KEY (patientId)
      REFERENCES patients(id),
  )

  ```

  > SELECT p.* , pd.* , d.* FROM patient_doctors pd
    JOIN doctors d ON d.id = pd.doctorId
    JOIN patients p ON p.id = pd.patientId