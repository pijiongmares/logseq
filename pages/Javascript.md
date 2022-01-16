- Description : Javascript notes
-
- ## What Is Javascript
	- Is a scripting language
	- Doesn't have the same features as other programming languages (c++, java)
	- Adds behavior and interactivity
	- Cannot communicate directly with a database, or file system on a computer
	- Great in manipulating web pages
	- Official name for javascript is ecmascript
- ## hello world
	- Display "hello world" as an alert message
	- Always put the javascript tag in the bottom of the body. ui should be loaded 1st before the script starts
	- ``` html
	  <!DOCTYPE html>
	  <html>
	  <head>
	   <meta charset="utf-8" />
	   <title>hello, world</title>
	  </head>
	  <body>
	   <script>
	  	 alert("hello world");
	   </script>
	  </body>
	  </html>
	  ```
- ## Basic Syntax And Structure
	- Javascript is case sensitive
	- Contains many statements, all ending with a semicolon
	- Not sensitive to whitespace or line breaks
	- Oneline comment :
		- ``` js 
		  	//one line comment
		  ```
	- Multiline comments :
		- ``` js 
		  	/*
		  multiline comment
		  	*/ 
		  ```
	- Javascript runs from top to bottom
- ## Variables
	- Javascript is a dynamic typed language (performs type checking at runtime)
	- ### var
		- Declare a variable using **"var"**
		- It can be re-declared and updated
		- ``` js 
		  	var myVariable;
		  	myVariable = 10;
		  	myVariable = "test";
		  ```
		- Hoisting is a javascript mechanism where variables and function declarations are moved to the top of their scope before execution.
		- ``` js 
		  	console.log(myName);
		  	var myName = "Philip";
		  ```
		- Problem with **"var"** is that if the variable was defined before and, not knowingly, it was defined again after somewhere in the code, this will make the output different as expected. for example :
		- ``` js 
		  	var greeter = "say hi";
		  	var times = 4;
		  
		  	if (times > 3){
		  var greeter = "say Hello instead";
		  	}
		  
		  	console.log(greeter); //prints "say Hello instead"
		  ```
		  
		  the "greeter" variable will be changed as **"var"** is an global scoped unless it is inside a function. this happens because **"var"** can be re-declared and updated.
	- ### let
		- Preferred for variable declaration
		- It is a block scope. a block lives in curly braces "{}"
		- ``` js 
		  	let greeter = "say hi";
		  	let times = 4;
		  
		  	if (times > 3){
		  let hello = "say Hello instead";
		  console.log(hello); //prints "say Hello instead"
		  	}
		  
		  	console.log(hello); //prints "hello is not defined"
		  ```
		- **"let"** can be updated but not re-declared
		- The same name variable can be declared in a different scope even if the other scope is more global compared to the other
	- ### const
		- Use to declare constant variable
		- Constant variable share some similarities with **"let"** declarations
		- **"let"** and **"const"** can only be accessed within the block they were declared
		- **"const"** cannot be updated nor re-declared
		- **"const"** must be initialized at the time of declaration
		- Constant objects cannot be updated but the values inside can.
- ## Math Operations
	- Use "=" for assignment of variables
	- "+" addition
	- "-" subtraction
	- "/" division
	- "\*" multiplication
	- If the statement is ""My age is " + 33", javascript concatenates the string to the numeric value
	- "5 * "a string"" returns "NaN" that means Not a Number
- ## Shorthand Math Operations
	- Use "+=", "-=", "\*=", "/=" to perform the operation then assign to the numeric variable
	- Use "++" or "--" to increment or decrement respectively the numeric value of the variable
- ## Logging To The Console
	- Use console.log() to print the value to the console
- ## Booleans
	- true/false
	- ``` js 
	  	var isEditable = true;
	  ```
- ## Control Flow And Logic
	- if, else if, else
- ## Comparison Operators
	- >
	- \>=
	- <
	- <=
	- == or != (is value equal/not equal)
	- \=== or !== (is value and type equal/not equal)
- ## Logical Operators
	- && and
	- || or
- ## While Loops
	- ``` js 
	  	while (condition){
	  
	  	}
	  ```
- ## For Loops
	- ``` js 
	  	for (i = 1; i < list.length; i++){
	  
	  	}
	  ```
- ## Break And Continue
	- Break will end the entire loop
	- Continue will stop the loop then continue to the next item
- ## Functions
	- Functions allow exceeding arguments but are omitted
	- ``` js 
	  	function getAverage(firstNumber, secondNumber)
	  	{
	  var average = (firstNumber + secondNumber) / 2
	  console.log(average);
	  return average;
	  	}
	  
	  	var result = getAverage(1, 2);
	  	console.log(result);
	  ```
- ## Working With Numbers
	- Use Math.round() to roundup a decimal value
	- Math.floor() to rounddown what ever value in the decimal place
	- Math.ceil() to roundup what ever value in the decimal place
	- Math.max() get the highest value
- ## NaN
	- Not a number
	- isNaN() check if value is not a number
- ## string
	- .toUpperCase() convert string to upper case
	- .toLowerCase() convert string to lower case
	- .indexOf get the index of a value in the string, returns -1 if not found
	- .slice(fromIndex, beforeIndex)  extracts the value in a string
	- .split(delimiter) splits the string into an array
- ## arrays
	- ``` js 
	  	var arr = [];
	  	arr[0] = true;
	  	arr[1] = "test";
	  	arr[2] = 2.2;
	  ```
	- ``` js 
	  	var arr = [10, 20, 30, true, "test"];
	  ```
	- ``` js 
	  	var arr = new Array();
	  ```
- ## objects
	- Javascript uses objects
	- Strings, numbers, arrays, etc.
	- This is an example of creating an object :
	- ``` js 
	  	var car = new Object();
	  	car.maxSpeed = 50;
	  	car.driver = "Philip"
	  	console.log(car.driver); //prints "Philip"
	  	car.drive = function(){
	  console.log("now driving");
	  	};
	  	car.drive(); //prints "now driving"
	  ```
	- Here is an example of object literal
	- ``` js 
	  	var car = {
	  maxSpeed: 50,
	  driver: "Philip",
	  drive: function(speed, time){
	  	console.log(speed * time);
	  }
	  	};
	  	car.drive(100, 2); //prints "200"
	  ```
- ## this keyword
	- Refers to the current object it was called
	- console.log(this) //prints the root window document of the html
	- ``` js 
	  	var car = {
	  test: function(){
	  	console.log(this);
	  }
	  	};
	  	car.test(); //prints the car instance object
	  ```
# constructor function
- variable name is in upper case
  ``` js 
  	var Car = function(maxSpeed, driver){
  this.maxSpeed= maxSpeed;
  this.driver = driver;
  drive: function(speed, time){
  	console.log(speed * time);
  }
  	};
  
  	var car = new Car(100, "Philip");
  	car.drive(50, 3); //prints 150
  ```
- or 
  
  ``` js 
  	function Car(maxSpeed, driver){
  this.maxSpeed= maxSpeed;
  this.driver = driver;
  drive: function(speed, time){
  	console.log(speed * time);
  }
  	};
  
  	var car = new Car(100, "Philip");
  	car.drive(50, 3); //prints 150
  ```
# date object

``` js 
	var today = new Date();
	console.log(today); //prints the current date and time
```
- can also set date manually
  
  ``` js 
  	var myBirthday = new Date(1988, 03, 12);
  	console.log(myBirthday); //prints the date and time set
  ```
# dom object
- an application programming interface
- use the dom when interacting with web pages
- add, delete, or change the content on a html document
- objects are elements, every html element in the doucment is an object
- document.getElementsByClassName("") used to retrieve all element objects that have the given class name, returns an array
- document.getElementsByTagName("") used to retrieve all element objects of the given tag name
- document.getElementById("") get element object by id
# changing content using the dom
- select the element object
- .innerHTML set/get the html value of the selected element
- .textContent set/get the text value of the selected element
# changing element attributes
- select the element object
- .getAttribute("") get the value of the given attribute
- .setAttribute(attributeName, value) set the value of the given attribute
- .className set/get the class of an element object
- .href get the url of the link
- .style get the css style object
# changing style
- select the element object
- .setAttribute("style", styleValue) set the value for the style attribute, replaces the whole value
- .style.\<css property\> set style value explicitly
# adding elements to dom
- select the element object
- .createElement("") add the element to the selected element object
- .appendChild("") append the new element
- .insertBefore(elementToAdd, beforeElement) insert before an element
# removing from the dom
- select the element object
- .removeChild(selectedChild) removes the selected child element in the selected parent element
# javascript events
- attribute in an element onclick is an example of event
- events are mostly done in the javascript block or file
  ``` js 
  	var title = document.getElementById("page-title");
  	title.onclick = function(){
  alert("title clicked");
  	};
  	title.onmouseover = function(){
  alert("mouse hover over title");
  	};
  ```
# button onclick event

``` js 
	var content = document.getElementById("content");
	var button = document.getElementById("show-more");

	button.onclick = function(){
if (content.className == "open"){
	content.className = "";
}else{
	content.className = "open";
	button.innerHTML = "Show Less";
}
	};
```
# window onload event
- to ensure that all dom are loaded before the javascript are executed, use onload event
  
  ``` js 
  	function setUpEvents(){
  var content = document.getElementById("content");
  var button = document.getElementById("show-more");
  
  button.onclick = function(){
  	if (content.className == "open"){
  		content.className = "";
  	}else{
  		content.className = "open";
  		button.innerHTML = "Show Less";
  	}
  };
  	}
  
  	window.onload = function(){
  setUpEvents();
  	}
  ```
# timers
- setTimeout(function, millisecond) delays the execution of the function
  
  ``` js 
  	var message = document.document.getElementId("message");
  
  	function showMessage(){
  message.className = "show";
  	}
  
  	setTimeout(showMessage, 3000);
  ```
- setInterval(function, millisecond) recurring function
- clearInterval(intervalObject) stops the currently running timer
  ``` js 
  	var colorChanger = document.document.getElementId("colour-changer");
  	var colours = ["red", blue, "green", "pink"];
  	var counter = 0;
  
  	function changeColor(){
  
  if (counter >= colours.length){
  	counter = 0;
  }
  
  colourChanger.style.background = colours[counter];
  counter++;
  
  	}
  
  	var intervalTimer = setInterval(changeColor, 3000);
  
  	colorChanger.onclick = function(){
  clearInterval(intervalTimer);
  	}
  
  	setTimeout(showMessage, 3000);
  ```
# accessing form elements
- var form = document.forms.\<form name\>
- form.name.value set/get the value of the input element with name attribute inside the html form
- can also set/get events
# javascript libraries
- general purpose
- animation
- form enhancement
- video