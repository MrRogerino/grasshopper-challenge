# grasshopper-challenge

 
 **1. Describe a ```for``` loop in 150 characters or less, and as simply as possible.** 
  * A ```for``` loop is used to execute the same code-- doing something repeatedly-- multiple times. For example, let's translate our general eating habits into code. 
    ```javascript
    // Until we are full, let's eat some food! 
    for (var belly = 0; belly < 100; belly += 20) { 
      eatSomeFood(); // Execute this repeatedly 
    }
    ```
    A ```for``` loop has three parts to it, each separated by a semicolon ```;```. First, we declare a variable ```belly``` to keep track of how full we are, and set its initial value to 0. Second, we define our exit condition (or else we'd be stuck in an [infinite loop!](https://gph.is/2cAmC66)): when our ```belly``` variable exceeds 100, we are "full" and exit the loop. Third, we state what will change every time we run through this loop. Here, our ```belly``` is getting fuller by 20-- thus, we would ```eatSomeFood()``` 5 times until we are "full". 

##

**The [Abstract Syntax Tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree) of code can be queried using ESquery. For example, the 6 value in the code below can be queried like this**:

Javascript:
```javascript
var answer = 6 * 7;
```
ESquery:
```Esquery
VariableDeclaration [left.value=6]
```
**2. Can you figure out how to reference the multiplier from the code above using ESquery?**
* A: ```VariableDeclaration [init.operator="+"]```. 
	At first glance, ESquery seems similar to traversing JSONs, or a DOM tree. Since there is only one ```VariableDeclaration```, I assume that all ```VariableDeclaration``` would refer to the one line. I am curious as to how to distinguish between multiple variable declarations. Since [left.value] seems to able to traverse down the tree and find the first instance of ```left```, I assume that ```init``` would find the first instance of init. Since ```operator``` points to the value that we want, and ```operator``` is a "child" of ```init```, I would check if ```init.operator``` is equal to ```+```.  
 
 ##
    
**3. Create 5 fun lesson ideas for teaching students what a Function is and how to use it - where each lesson is completed remotely by a user on their mobile phone.**

##### Lesson 1:  Let it Go

Users start with multiple functions already declared. Each function prints out a certain line of a song; in my example, we're going to sing "Let It Go". The idea is to have users recreate the chorus by calling the provided functions in the correct order and get used to calling functions. For now, each function will take no arguments. **BONUS**: Now, rather than having a ```letItGo``` method that takes no arguments, change it to accept one argument (```letItGo(number)```) which will have it repeat "Let It Go" multiple times depending on the argument provided; challenge users to restructure their code to handle this new change.  

```javascript
console.log("Let it go!") // Prints out "Let it go!"
function letItGo () { // We declare a function
	console.log("Let it go!"); // When called, it will execute whatever is inside the curly braces
} 
letItGo(); // To call a function, simply reference it by name, and make sure to add the parenthesis afterwards! 

// Series of functions that print out lines to the chorus 
// Chorus lyrics here
// Instructions: If you somehow don't already know the lyrics to Let It Go, reference the text above, then call the functions provided in the correct order
```

##### Lesson 2: Bad Service 

Users start with a basic tip calculator function defined, which accepts a dollar amount and returns 15% of the number as tip. The challenge is for the user to add a new parameter, ```serviceRating```, which will be a number from 0-5, with 5 meaning excellent service, and 0 corresponding to that apathetic, gum-chewing waiter on their seventh shift in six days. For each rating point, up the tip rate by 1%, to reward exception service. This will get users some experience with adding functionality to existing code, introducing new variables, and resetting the value of a variable (```tipRate```). 

```javascript
// this is our original basic tip calculator
function tipCalculator(bill) { // this function accepts one parameter, which we reference as "bill"
	var tipRate = 0.15; // We declare a variable called tipRate and set its value to 0.15
    return bill * tipRate;
}
tipCalculator(100) // Returns 15 
tipCalculator(200) // Returns 30

function add(x,y,z) { // A function with multiple parameters, each separated by a comma
	return x+y+z;
}
add(3,4,5) // Returns 12

var number = 2 // number equals 2
number += 2 // number equals 4

// Your code for an advanced tip calculator here
// If struggling, can give general infrastructure like so: 
function advancedTipCalculator(bill, rating) { 
	// Your code here
}
```

##### Lesson 3: Beep Boop? 

Wall-E seems to have been infected with some malware, and has started speaking in tongues; he seems to be saying every word backwards. Users must create a function to help decipher what he's trying to say. Users are introduced to some built-in methods for strings and arrays-- ```String.split(), Array.reverse()```, and ```Array.join()```-- and must figure out how to use them together to reverse a word. This lesson introduces the concepts of method chaining and built-in methods. Alternatively, users must figure out how to reverse a word without using any built-ins, but rather with a ```for``` loop. This can help introduce the concept of string indexing. 

```javascript
var string1 = "hello" // a String
string1.split("") // Returns [ 'h', 'e', 'l', 'l', 'o' ]

var array1 = ['a','b','c']
array1.reverse() // Returns ['c','b','a']
array1.join() // Returns 'abc'

// Methods can be chained together
// All that matters is that you are calling a function on the right "type"  
string1.reverse() // Will return an error because reverse is an Array function

function decipher(word) {
	// Your code here
}

decipher('elloh') // Should return 'hello'
```

##### Lesson 4: Animal Farm 

Users start with an array of animal noises and a function ```animalFinder(noise)``` that returns the animal corresponding to each noice. The challenge is to create a function that takes an array of animal noises and returns an array of the animals that make those noises. This will increase familiarity with loops, iterating over arrays, as well as introduce the concept of callbacks (shown afterwards as part of the "optimal" solution). This can also be an opportunity to introduce another popular built-in method: ```Array.map()```

```javascript
var animalFarm = ['moo','cluck','oink','oink','moo','moo']

function animalFinder(noise) { 
  	// This is a Hash, or Object 
	animalNoises = { 'moo':'cow', 'cluck':'chicken', 'oink':'pig'} // Don't worry if this doesn't make too much sense yet
  	return animalNoises[noise]; // Given a noise, will try to find its matching value within animalNoises
}

animalFinder('moo') // Returns 'cow'
animalFinder('cluck') // Returns 'chicken'

function oldMcDonald(farm) {
	// Your code here
}

oldMcDonald(animalFarm) // Should return ['cow','chicken','pig','pig','cow','cow']
```
##### Lesson 5: Just My Type

Users are shown an example of how to prototype a function by referencing the Wall-E example to prototype the ```String``` function 
necessary to solve Lesson 3. They are then challenged to create their own prototyped function. In this lesson, they will build a function that sorts a string in reverse alphabetical order. This lesson will illustrate how powerful reusable code can be, as well as incorporate some more method chaining.

```javascript
Array.prototype.print = function() { // Allows you to call a function called 'print' on any Array 
    // executes any code here 
    console.log(this); // 'this' is a keyword used to refer to the Array that is calling print
}
var array2 = ['hello','world']
array2.print // Prints [['hello','world']

// For what type of object are we prototyping for here? 

// If struggling, can give hint like this:
String.prototype.decipher = function() { 
	// Your code here
}
```
##
**4. Describe, in detail, what this code is doing:** 
```javascript
var cost = [2,10,17,50];
var total = 0;
function aFunction (a){
	for (var element of a){
		total = total + element;
	}
	return total;
}
```
* A: Two variables are being declared: ```cost```, which is an array of four numbers, and ```total```,  an integer 0. We then declare a function ```aFunction```, which takes in one parameter ```a```. When called, the function iterates through all elements of ```a``` and adds each element to the ```total``` variable  declared on line 2. An important distinction here is that ```aFunction``` is never called, only defined. Additionally, since ```total``` is declared in the global context, each call of ```aFunction``` would keep adding to the same total (i.e calling ```aFunction(cost)``` once would return 77, calling it twice would return 154). 
