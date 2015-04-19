![General Assembly Logo](http://i.imgur.com/ke8USTq.png)

# Javascript Scope

## Objectives

By the end of this, students should be able to:

- Understand compiled vs interpreted languages, in order to understand scope.
- Understand Lexical Scope.
    - How variables are declared using Lexical Scope.
    - How it's constructed.
- Know that Javascript only provides Global and Function Scope.
- Understand how variable hoisting follows from Lexical Scope.

## Instructions

## Compiled and Interpreted Languages.
[Compiled and Interpreted Languages](Compiled_Interpreted_Languages.md)

## I Do

Draw diagrams that show this process. 

### Javascript Phases.

The Javascript Virtual Machine (VM) performs many operations to go from text in file, i.e. code, to 1's and 0's that are stored in Memory and executed by a CPU.

The phases are:  

- Load: Load the javascript file.
- Compilation: Compile javascript code in a file to a form that can be executed.
- Execution: Run the javascript program.

Part of the Compilation phase is Lexical Analysis. In general, Lexical Analysis scans through the source code, one character at a time, looking for language constructs like variables, functions, built-in keywords, etc.

During this time the compiler also looks for variable declarations in the source code and build **Variable Scopes**. Scope is *part of* **Execution Context(EC)**.  EC provides a Context for the next phase, Execution.

## Building Scope.

Scope is built during the Lexical Analysis part of the Compilation phase. When this is done it's called **Lexical Scope**. This is very common in many programming languages.

Let's see how it works, eh. Heres the code we'll work with.  

```javascript
var firstName = 'John'; // 1
var lastName = 'Dowd'; // 2
var age = 19; // 3

function displayPerson(fname, lname){ //4, 5
  var prefix = 'Mr'; // 6
  var fullName = null; // 6

  function getFullName(){ // 7
    var suffix = "Esq.";  // Everybody's a lawyer, eh.
    return  fullName = prefix + " " + fname + " " + lname + " " + suffix;
  };

  return getFullName();
};

function removeYears(){ // 8
  var minusYears = 10, age = 49;
  return age - minusYears;
};

console.log(displayPerson(firstName, lastName));
console.log(removeYears());

```

* Node will load this file and pass the source code on to it's Javascript VM.

* The VM will run do a Lexical Analysis of this source and build Variable Scope as follows:

    1) Found 'var firstName' variable declaration.  
    Put firstName variable in Global Scope.  
    2) Found 'var lastName' variable declaration.  
    Put lastName in Global Scope.  
    3) Found 'var age' variable declaration.  
    Put age in Global Scope.  
    4) Found 'var displayPerson' declaration.  
    Put age in displayPerson in Global Scope. 
    
    **Notice that displayPerson's value is a function. So, create a inner scope and process this function.**
    
    5) Found the fname and lname declarations.
    *Note: functions arguments behave just like local variables.*    
    Put them in the displayPerson function scope.  
    6) Found prefix, fullName variable declarations.  
    Put them in the displayPerson function scope.  
    7) Found getFullName declaration.  
    Put getFullName in the displayPerson function scope.
    
    **Notice that getFullName is a function. So, create an inner scope and  process this function.**
    **All done with getFullName function, no more variable declarations.**
    **All done with displayPerson function, no more variable declarations.**

    ![Scope](JS_Scope1.png)

    8) Found removeYears variable declaration.
    Put removeYears in Global scope.  

    **Notice that removeYears value is a function. So, create a inner scope and process this function.**

    9) Found age and minusYears variable declarations.  
    Put these in the function's scope.
    
    ![Scope](JS_Scope2.png)

## You Do.
For the following code enumerate how scope is built and draw a diagram of this scope. *As I have done above*

Work in teams.

Compare the above with another team's deliverable.

**Need some example code here!!!**

## We do

### Execute Code

```
var firstName = 'John'; // 1
var lastName = 'Dowd'; // 2
var age = 19; // 3

function displayPerson(fname, lname){ // 6, 7
  var prefix = 'Mr'; //6, 7
  var fullName = null;  //6, 7

  function getFullName(){ 
   return  fullName = prefix + " " + fname + " " + lname + " " + suffix; //
  };

  return getFullName(); // 8, 9
};

function removeYears(){ 
  var minusYears = 10, age = 49;
  return age - minusYears;
};

console.log(displayPerson(firstName, lastName)); // 4, 5
console.log(removeYears());

```
**Now we'll look up variables in the inner Global scope.**

1) Lookup firstName in GlobalScope. Set it's value to 'John'.  
2) Lookup lastName in GlobalScope. Set it's value.  
3) Lookup age in GlobalScope. Set it's value.  
4) Lookup displayPerson, firstName and lastName in GlobalScope.  
5) Execute displayPerson function.  

**Now we'll look up variables in the inner displayPerson scope.**  

6) Lookup fname, lname, prefix, fullName in displayPerson scope.  
7) Set there values.  
8) Lookup getFullName in displayPerson scope.  
9) Execute getFullName function.  

**Now we'll look up variables in the inner getFullName scope.**  
  
10) Lookup fullName, prefix, fname and lname variables in getFullName scope. NOT FOUND.  
10.1) Lookup fullName, prefix, fname, lname variables in displayPerson scope. FOUND. Get their values.  


11) Lookup suffix in getFullName scope. NOT FOUND.  
11.1) Lookup suffix in displayPerson scope. NOT FOUND.  
11.2) Lookup suffix in outer, Global, scope. NOT FOUND.   
11.3) Cause a reference error.  


#### Remove suffix and continue.

## Bonus (Optional Section)

If you're looking for extra challenge or practice once you've completed the above, try to...

## Notes

Gotcha's and extra information

## Additional Resources

List additional related resources such as videos, blog posts and official documentation.

- Item 1
- Item 2
- Item 3
