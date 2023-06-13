# Intro to JavaScript
01. Which keywords are used to declare a variable in JavaScript?

    > let, var, and const

02. What is the definition of a function?

    > A function is a subprogram created to complete a specific job.

03. What are the `SOLID` principles?

    > 

04. Given this array: How could you remove the `pineapple`?

    ```js
    let fruit = ['apple', 'banana', 'pineapple', 'orange', 'strawberry']
    ```

    > fruit.splice[2, 1]

05. Given these two objects: How could you add each to the others friends arrays?

    ```js
    let you = {
        name: "You",
        hair: true,
        friends: []
    }
    let them = {
        name: "Them",
        hair: false,
        friends: []
    }
    ```

    > you.friends.push(them.name)
      them.friends.push(you.name)

06. Give an example of a JavaScript `Conditional`:

    > if (i == 1) {
        console.log('true')
      }

07. What is the main difference between `parameters` and `arguments`?

    > An argument is the value given to the function, whereas parameters are the values given when defining a function.

08. Instead of writing everything to the console, what is a better way to debug your code?

    > You can use the developer tools.

09. What is the difference between a `primitive` value and a `reference` value?

    > A primitive value is a number, string, or boolean, whereas a reference value is an array or object.

10. Demonstrate a loop that prints the numbers between -100 and 100?

    > for (let i = -100; i <= 100; i++) {
        console.log(i)
      }