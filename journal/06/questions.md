# Single Page Applications with Vue
01. What is the entrypoint of an application?

  > main.js is the entrypoint of an application.

02. What is the difference between a vue `component` and `page`?

  > A vue component is broken up pieces of a page.

03. What is ***Component-Based Architecture***?

  > Component-Based Architecture is a way to break up larger U.I. into smaller self-containing pieces.

04. What are the three tags that make up a Vue component?

  > template, script, and style

05. What are ***lifecycle hooks***? What are lifecycle hooks used for?

  > Lifecycle hooks are functions that are called in different states of the page. They are good for running functions specifically when the page hits a certain state such as on creation or on mounting.

06. Which component in Vue does the vue-router use to mount pages onto?

  > The vue-router uses main.js to mount pages onto it with a .mount().

07. What is the difference between the `AppState` and the state object within a component?

  > The AppState is global for all vue files to use whereas the state is scoped to the file it is in.

08. What is the responsibility of `Services` in our Vue projects?

  > The service is used for http requests and manipulating data.

09. What are ***props*** and how are they used? Provide an example

  > Props are variables that can be transferred from a parent vue file to a child vue file. An example of this is if you want to get a component card for each object in an array you would pass each object as a prop.

10. What is the Vue method used to create watchable objects such as `state` or `AppState`?

  > The method used to create watchable objects is reactive()