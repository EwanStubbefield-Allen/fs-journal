# JavaScript

<!-- SECTION Array Methods -->
  let variable = array.find(object => conditional) --> finds the first object that meets condition
  let variable = array.findIndex(object => conditional) --> returns the object's index that meets condition
  let variable = array.filter(object => conditional) --> creates array with all objects that meet condition
  let variable = array.sort((a, b) => a.key - b.key) --> creates array that sorts objects based on key
  let variable = array.map(object => math) --> combines all content with math
  let variable = array.shift() --> removes first item from array and stores it
  let variable = array.pop() --> removes last item from array and stores it
  let variable = array.slice(firstPosition, lastPosition) --> returns section from firstPosition to last
  array.forEach(object => {do something to each object}) --> changes each object
  array.split(when to split) --> breaks up objects into array
  array.join(between each item) --> creates a string from array
  array.unshift(variable) --> puts variable at beginning of array
  array.push(variable) --> pushes variable to end of array
  array.includes(variable) --> returns a boolean if array contains variable

<!-- SECTION Object Methods -->
  let object { ...previous object } --> dumps all previous object into object
  Object.values(object) --> returns values in an array
  Object.keys(keys) --> returns keys in an array

<!-- SECTION Math Methods -->
  Math.random()
  Math.floor(number) --> rounds number down
  Math.ceil(number) --> rounds number up

<!-- SECTION String Methods -->
  string.toUpperCase() --> uppercase all character
  string.toLowerCase() --> lowercase all character

<!-- SECTION Number Methods -->
  variable.toString() --> turns number to strings
  variable.toFixed(number) --> adds required amount of numbers after decimal

<!-- SECTION Window Methods -->
  window.alert(text) --> window with text
  window.confirm(text) --> allows window to have option
  window.prompt(text) --> allows user to type in window
  window.location.reload(text) --> refreshes page
  window.event.preventDefault() --> prevents the default action

<!-- SECTION Special Functions -->
  setInterval(function or {() => code}, ms) --> runs function repeatedly every ms