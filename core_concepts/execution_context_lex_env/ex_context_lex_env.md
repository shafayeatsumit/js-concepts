# Conceptual Aside
    # Syntax Parsers
    # Lexical Environments
    # Execution Contexts

## Syntax Parsers
           A PROGRAM THAT READS YOUR CODE AND DETERMINES WHAT IT DOES AND IF ITS GRAMMER IS VALID
## Lexical Environments
            WHERE SOMETHINGS SITS PHYSICALLY IN THE CODE YOU WRITE. Whrere it's written and what surrounds it.
   
+ where you write something is important
+ where you see things written gives you an idea of 
+ where it will actually sit in computers memory 
+ how it will interact with other functions and variables 
+ compiler cares about where you put things

## Execution Context:
         A WRAPPER TO HELP MANAGE THE CODE THAT IS RUNNING

There are lots of lexical environments. Which one is currently running is managed via execution contexts. 

# Execution Context (Global: not inside a function)
    # Whenever we write a JS code an execution context will be created and run. The base execution context is the `global
    execution context`
    
### Global Execution context creates 2 things for us
       1) Global Object
       2) special variable called `this`
       
 Javascript engine creating this 2 things for you whenever the code is run. Because the code is wrapped inside the execution
 context.
 
 ## Window Object
     Whenever we create a global variable or function we are actually creating a property of the global object. In the case of browser the
     global object is window object!

There are 2 happening when you run a Js code. `compilation` and `interpretation`. In the `compilation` phase no assignment 
operation will be happened. And in the `interpretation` phase the actual execution will take place.

### Hoisting (execution context creating and hoisting)
what is hoisting? 

>>**variables and functions setup in the memory space before executing the code**
```js
b();
console.log(a);

var a = 'Hello World!';

function b() {
    console.log('Called b!');
}
// output  
    //called b
    //undefined

```              
             

+ execution context is created in two phases
+ 1. creation phase: Global Object, This setup in memory.
+ in this phase the parser Setup memory space for vars functions this is hoisting.

Before your code starts executing line by line the JS Engine set aside memory space for the variable that you created in the entire code and all of the functions you created .So those functions and vars exists in memory.  so when the code starts executing it can access them. 
For variable it's a bit different. 

+ 2. when the execution phase is started then we assign variable values. Before it was just initiated.


#### Execution Context
as we know we have two phase in Execution Context.

+ creation phase: where we  setup variables and functions.
+ execution Phase: running the code line by line.

##### Single threaded & Synchronous 
single threaded -> one command at a time
synchronous -> Line by line (in order)
JS is single threaded synchronous execution .

#### execution stack (call stack)

Any time you execute or invoke a function a new execution context is created and put on the stack. whatever at the top of the stack is currently running.
[see image.](<https://gist.githubusercontent.com/shafayeatsumit/0e9251bbddefc3390ff88456d197ccdd/raw/6a698e26c404e72403f269a23c29aed2fe374430/h)%2520context.png>)

##### variable environment 
>where is the variable
##### scope chain
>every execution context has a reference with it's outer environment \
>scope means where the variable is available in your code \
>scope chain is the outer reference that a running function has.
>
+ lexical environment comes into play when it requires to connect to outer environment. 
+ in the example function b lexically sits in the Global environment. so myVar will find Global value of myVar.


#### Asynchronous 
More than one at a time.

