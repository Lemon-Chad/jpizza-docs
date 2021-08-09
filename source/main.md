
# Main Documentation

## Comments

Comments are statements that the programming language ignores.
You can declare comments in JPizza using two angle brackets facing away from each other.

You can also make multiline comments using two left facing angle brackets as the opening and closing.

You can exit single line comments early using a semicolon.

```jpizza
<> This is a comment.
<> This comment stops; "here.";

<<
This is a multiline comment.
Isn't it cool?
<<
```

## Statements

Code in JPizza is made up of statements, which can be any form of expression. To end a statement,
you must end it with a semicolon.

```jpizza
"This is a statement";
2 + 2;
3 + 4
<> No semicolon! This will cause an error!
```

## Operators

JPizza has many operators, a list can be found below.

### Binary Operations

Binary operations take in two operands.

- `+` - Adds the operands together.
- `-` - Subtracts the right operand from the left.
- `*` - Multiplies the operands together.
- `/` - Divides the left operand by the right.
- `^` - Raises the left operand to the power of the right operand.
- `%` - Gets the left operand modulo the right operand.
- `x=` (*where x is any binary operation*) - Assigns the left operand, assuming it is a variable, to the 
  result of the binary operation `x`.

### Unary Operations

Unary Operations only take in one operand.

- `x++` - Increments `x` and assigns the value to `x`, assuming it is a variable.
- `x--` - Decrements `x` and assigns the value to `x`, assuming it is a variable.
- `--x` - Returns the decremented value of `x`.
- `++x` - Returns the incremented value of `x`.
- `-x` - Gets the negative value of `x`.
- `!x` - Inverts `x`.

### Conditional Operations

- `&` - Checks if both the left operand, and the right operand are true.
- `|` - Checks if either the left operand, or the right operand is true.
- `>` - Checks if the left operand is greater than the right operand.
- `>=` - Checks if the left operand is greater than or equal to the right operand.
- `<` - Checks if the left operand is less than the right operand.
- `<=` - Checks if the left operand is less than or equal to the right operand.
- `==` - Checks if the left operand is equal to the right operand.
- `!=` - Checks if the left operand is not equal to the right operand.

## Variable Assignment

Variables are defined using the keywords '**var**' and '**bake**'.

**Bake** permanently sets a variables value, to where it cannot be changed.

After variables are defined, they can be set with the **var** keyword omitted. 
This will set the variable of the same name in the most recent scope.

```jpizza
var x  => 3;
bake y => "Hello!";
x => 4;
y => "Goodbye!"; <> Throws an error since y is a baked variable.
```

There is also a unique type of variable known as a callback variable.
This type of variable does not store a value, but instead stores its expression.
Whenver it is referenced, it returns the computed expression.

This can be compared to macros in other languages, like C.

```jpizza
var x => 4;
cal y -> x ^ 2;

println(y); <> Prints 16, since x^2 is currently 16.

x => 8;
println(y); <> Prints 64, since x^2 is now 64.
```

An additional feature for variables is static typing.

Although JPizza is dynamically typed, meaning that variables can store any type of data, 
you can statically type them using the hash operator followed by the variable type.

```jpizza
var x#num => 4;
<> Sets the type of variable x to be a number.

x => 8; <> Ok!
x => "Hello!"; <> Error!
```

## Lists

Lists are, simply put, a list or array of values.

Lists are defined using square brackets. Inside the brackets are each element,
seperated by a comma.

List elements can be accessed by enclosing the index you want to access in square brackets
following the list.

Items can be appended to the list using the modulo operator, and removed using the division operator.

You can extend lists by other lists using the plus operator.

```jpizza
var list => [1, 2];

println( list[0] );
<> Prints the first element of the list, which is 1 in this case.

list += [3, 4];
<> Extends the list with the elements 3 and 4.
println( list );
<> Prints [1, 2, 3, 4]

list /= 3;
<> Removes 3 from the list.
list %= 6;
<> Adds 6 to the list.
```

## Dictionaries

Dictionaries are a set of keys and values, like a word dictionary. In the case of the English dictionary,
the keys would be words, and the values would be the definitions.

Dictionaries can be declared using braces. 
Inside these braces each key and value should be defined using the key followed by a colon and then the value.
Each pair should be seperated by a comma.

You can get the stored value of a key by enclosing the key in square brackets following the dictionary.

You can set key value pairs by using the set function, and you can delete keys using the delete function.

```jpizza
var coolDict => {
    "abc": 123,
    "Hello": "world."
};

set(coolDict, "Hello", "world!");
<> Sets the value of the key "Hello" from "world." to "world!".

delete(coolDict, "abc");
<> Removes the key value pair "abc": 123 from the dictionary.

println("Hello" + " " + coolDict["Hello"]);
<> Prints "Hello world!".
```

## Conditional Statements

### If Statements

If statements are declared using the '**if**' keyword. The if keyword should
then be followed with a true/false condition in parentheses, and then the body.

The body is the code that is run *if* the true/false condition is true. You can
use curly braces, (`{}`), to write multiple lines, but if you only want to write one
line braces are not necessary.

You can add additional branches to the statement using the '**elif**' and '**else**' keywords.

**Elif** statements are declared the same as if statements except with the '**elif**' keyword 
and should follow an (el)if statements body. These will run if the previous (el)if 
statement is false, and their condition is true.

**Else** statements are simply the '**else**' keyword followed by the bodyz.
Else statements should come after an (el)if statement, and they only execute if
the previous (el)if statement is false.

```jpizza
if (true) {
    println("This will always run!");
} elif (false) {
    println("This will never run. :(");
} else {
    println("If this ever runs, seek shelter immediately, 
             the world is ending.");
}
```

### Queries

Queries are a unique JPizza expression that is similar to a ternary in other languages, but cooler.

Query statements start with a question mark followed by a true/false condition.
This condition should then be followed with a colon and an expression.
This expression will be returned if the condition is true.

You can add additional branches to queries using the dollar sign followed by a condition.
Then simply follow the dollar sign with a colon and an expression.

To add a default branch, you can use a dollar sign and an underscore, (`$_`).

```jpizza
var input => nfield("Please enter a number: ");
<> Assigns a user chosen number to the variable input.

var query => ? input > 10 : "Number is awesome!"
             $ input <  5 : "Number is cool."
             $_           : "Number is meh...";

<> Assigns the value of the query to the variable query.
<> If the input is greater than 10, the value will be "Number is awesome!"
<> If the input is less than 5, the value will be "Number is cool."
<> If none of the above are true, the value will be "Number is meh..."
```

### Case Trees

Case trees are special statements that can quickly run code if two values are equal.
JPizza has two types of case trees, the famous switch statement and the special match
statement.

#### Switch

Switch statements allow you to pass in a value and run code based on if a given value is equal
to one of the cases. What makes switch statements special is their ability to fall-through, meaning
that once one case is matched, the code of all cases below it run until it reaches the '**break**' keyword
or runs out of cases.

To declare a switch statement, start with the '**switch**' keyword followed by the value you want to
compare in parentheses. Then follow it with curly braces, (`{}`).

Inside the braces are the cases. To declare a new case, start with the keyword '**case**' followed by
the value you want to check. Follow the value with a colon. Any code written afterwards up until the next case
statement will be run if the values are equal.

To add a default case, you can use the '**default**' keyword followed by a colon, and the code you want to
execute. Defaults cases are immune to fall-through.

```jpizza
switch (4) {
    case 1:
    case 3:
    case 5:
    case 7:
    case 9:
        println("Odd number!"); 
        break;
    <> Fall through makes it so that all the cases up until case 9 execute this code.
    
    case 2:
    case 4:
    case 6:
    case 8:
        println("Even number!");
        break;
    
    default:
        println("Unhandled number...");
    <> This will execute if the number is not in any of the above cases.
};
```

#### Match

Match statements are similar to switch statements in structure, but different in execution.
Match statements return a value when their case is matched, and they are immune to fall-through.

To declare a match statement, start with the '**match**' keyword followed by the value you want to
compare in parentheses. Then follow it with curly braces, (`{}`).

Inside the braces are the cases. To declare a new case, start with the keyword '**case**' followed by
the value you want to check. Follow the value with a temporary assignment arrow, (`->`) followed by the value you
want to return.

To add a default case, you can use the '**default**' keyword followed by an arrow, and the value you want to
return.

```jpizza
println(match (4) {
    case 2 -> 4
    case 4 -> 8
    case 8 -> 12
    
    default -> 0
});

<> Prints the matching value, which is 8 in this case.
```

## Loops

JPizza has 5 types of loops, standard loops, **for** loops, **iterative** loops, 
**while** loops, and **do-while** loops.

### Standard Loops

#### What is a Standard Loop?
Standard loops are loops that do not have any sort of condition, and simply repeat
code infinitely until it is stopped, either from inside the code or by the user.

#### How to Make a Standard Loop

To make a standard loop, we simply need to type the keyword '**loop**'.
Following the **loop** keyword, we need our body. The body is the code that is
executed during the loop.

JPizza offers two forms of bodies, the arrow form, and the braces form.

##### Arrow Form

Arrow form allows you to quickly write the loop on one line, and return a list
afterward. 

Using the assignment arrow, (`=>`), followed by an expression, we can
set the body to the provided expression.

Once the loop finishes, it returns a list in order of each evaluation of the expression.

```jpizza
var index => 0;
var lp => loop => if (index > 5) break; 
                    else index++;

<<

This assigns lp to the value of the loop.
The loop increments the value index until it is greater than 5.
This returns a list of [1, 2, 3, 4, 5, 6].

<<
```

##### Braces Form

Brace form allows you to write multiple lines of code, but with no return value.

By following the condition of the loop with curly braces, (`{}`), we can use
brace form. Simply insert your code inside the braces to set it to the body.

```jpizza
var r;
loop {
  if ((r => random()) > 0.5)
    break;
  println(r);
}

<<

This loop prints random numbers until one is greater than 0.5.

<<
```

### For Loops

#### What is a For Loop?
For loops are a type of loop that runs code over a range of numbers, passing in
a variable for the current loop number.

#### How to Make a For Loop
For loops are denoted by the '**for**' keyword followed by parentheses.
Inside the parentheses will be the condition of the for loop. 

##### Condition

First start off with an identifier, like 'i'. This identifier will be the name of the 
variable that is passed into our code representing the current loop number. 

Following the identifier
we put a temporary assignment arrow, (`->`), which means that our variable will be dropped
after the loop ends.

Next we have our first number, then a colon followed by our second number. This represents our range.

Finally, for the body we have the option to put a step number in, which represents how much
we increase as we iterate. If we want to add this, we put the step arrow, (`>>`), followed by
how much we want to step.

##### Body

After we close the parentheses, we write our body. The body is what is executed
for each iteration.

JPizza offers two forms of bodies, the arrow form, and the braces form.

###### Arrow Form

Arrow form allows you to quickly write the loop on one line, and return a list
afterward. 

Using the assignment arrow, (`=>`), followed by an expression, we can
set the body to the provided expression.

Once the loop finishes, it returns a list in order of each evaluation of the expression.

```jpizza
var lp => for (n -> 0:3) => 2 ^ n;

<<

This assigns lp to the value of the for loop.
The loop iterates n over the range 0 to 3. It then evaluates to 2^n.
This returns a list of [1, 2, 4], as 2 ^ 0 is 1, 2 ^ 1 is 2, and 2 ^ 2 is 4.

<<
```

###### Braces Form

Brace form allows you to write multiple lines of code, but with no return value.

By following the condition of the loop with curly braces, (`{}`), we can use
brace form. Simply insert your code inside the braces to set it to the body.

```jpizza
for (i -> 3:5 >> 0.5) {
    println(i);
    <> Prints i for each iteration.
}

<<

This loop iterates i over the range 3 to 5.
As specified by our step arrow, it increases by 0.5 each time.
This ends up printing:
3
3.5
4
4.5

<<
```

### Iterative Loops

#### What is an Iterative Loop?

An iterative loop is a loop that iterates over a list of values.
It takes in an identifier and assigns a variable using that identifier to the
current element.

It's the same thing as writing a for loop that iterates over each index in a list
and then assigns a variable to the value at each index.

#### How to Make an Iterative Loop

Similarly to a for loop, it starts off with the keyword '**for**', followed by the condition.

##### Condition

The condition starts with an identifier, which will be passed into the body as our variable.
Follow the identifier with an iterator arrow, (`<-`), and then the value you want to iterate over.

##### Body

JPizza offers two forms of bodies, the arrow form, and the braces form.

###### Arrow Form

Arrow form allows you to quickly write the loop on one line, and return a list
afterward. 

Using the assignment arrow, (`=>`), followed by an expression, we can
set the body to the provided expression.

Once the loop finishes, it returns a list in order of each evaluation of the expression.

```jpizza
var lp => for (n <- [1, 2, 3]) => n + 2;

<<

This assigns lp to the value of the iterative loop.
The loop iterates over the list [1, 2, 3] and adds 2 to each.
This returns a value of [3, 4, 5], as 1 + 2 is 3, 2 + 2 is 4, and 3 + 2 is 5.

<<
```

###### Braces Form

Brace form allows you to write multiple lines of code, but with no return value.

By following the condition of the loop with curly braces, (`{}`), we can use
brace form. Simply insert your code inside the braces to set it to the body.

```jpizza
for (i <- ["Hello", "world!"]) {
    println(i);
    <> Prints i for each iteration.
}

<<

This loop iterates i over the list ["Hello", "world!"].
This ends up printing:
Hello
world!

<<
```

### While Loops

#### What is a While Loop?

While loops are no doubt the simplest type of loop. They simply take in a
true/false condition and repeat the code *while* the condition is true.

#### How to Make a While Loop

While loops start with the keyword '**while**', followed by the condition
in parentheses.

After the condition, we have the body. JPizza offers two forms of bodies, the arrow form, and the braces form.

##### Arrow Form
Arrow form allows you to quickly write the loop on one line, and return a list afterward.

Using the assignment arrow, (`=>`), followed by an expression, we can set the body to the provided expression.

Once the loop finishes, it returns a list in order of each evaluation of the expression.

```jpizza
var a => 1;
var lp => while (a < 10) => a => -(a + abs(a) / a);

<> The equation -(a + abs(a) / a) simply causes a to tesselate and iterate, as in:
<>  1 -> -2
<> -5 ->  6

<<

This assigns lp to the value of the while loop.
This loop executes the body while a is less than 10.
In the body it reassigns a until it is greater than 10.
This returns [-2, 3, -4, 5, -6, 7, -8, 9, -10, 11].

<<
```

##### Braces Form
Brace form allows you to write multiple lines of code, but with no return value.

By following the condition of the loop with curly braces, (`{}`), we can use brace form. Simply insert your code inside the braces to set it to the body.

```jpizza
while (true) {
    var r => random();
    if (r > 0.5) { break; }
    println(r);
}

<<

This loop executes infinitely until it encounters the break keyword.
First it assigns r to a random number between 0 and 1.
Next, it breaks the loop if r is greater than 0.5.
If the loop continues to run, it prints the random number.

<<
```

### Do-While Loops

*Please read the section on while loops before reading*

#### What is a Do-While Loop?

Do-while loops are very similar to while loops, except they run the body
before checking the condition, compared to checking the condition before running
the body. This causes do-while loops to run at least once before they stop.

#### How to Make a Do-While Loop

Do-while loops start with the keyword '**do**'. After **do**, 
we have the body, which can be defined the same as a while loop. Finally, we have
the '**while**' keyword, followed by the condition in parentheses. This should end
with a semicolon, since it is not a bracket. Your final loop should look something
like this:

```jpizza
do {
  println("This condition is false!");
} while (1 == 2);
```


### Keywords

Loops come with 2 special keywords, **break** and **continue**.

**Break** stops the loop instantly.

**Continue** skips the rest of the loops body and *continues* to the next iteration.

## Functions

### What is a Function?

Functions are special types that take in arguments, execute code using those arguments, and
return a value. They can be used to repeat certain pieces of code with different values each time.

### How to Make a Function

First, declare a new function with the '**fn**' keyword. 

#### Name

This should then be followed by the function name.
You can omitt the function name to make it anonymous. 
In the case of anonymous functions, it's better to use an exclamation mark to turn it into a lambda.

#### Arguments

After this, you put the name of each argument seperated by a comma inside of angle brackets, (`<>`). 
If your function takes in no arguments, the angle brackets can be omitted. 
Otherwise, there must be a space in between to prevent it from becoming a comment.

#### Body

##### Arrow Form
Arrow form allows you to quickly write the function on one line, and return a value afterward.

Using the temporary assignment arrow, (`->`), followed by an expression, we can set the return value to the provided expression.

```jpizza
fn addOne<x> -> x + 1;

<> This creates the function addOne, which takes in x
<> and returns x + 1.
```

##### Braces Form
Brace form allows you to write multiple lines of code, but with no automatic return value.

By using curly braces, (`{}`), we can use brace form. 
Simply insert your code inside the braces to set it to the body.

If you want to return a value, you must say it explicitly using the '**return**' keyword
followed by the return value.

```jpizza
fn add<x, y> {
    return x + y;
}

<> Creates the function add, which takes in x and y
<> and returns x + y.
```

### Using Functions

Functions can be called by typing the function name followed by parentheses. Inside the
parentheses is where the arguments go, each seperated by a comma. If there are no arguments,
the parentheses can remain empty.

```jpizza
println(addOne(5));
<> Prints 6, since 5 is passed in as x and addOne returns x + 1.

println(add(3, 4));
<> Prints 7, since 3 and 4 are passed in as x and y, and add returns x + y.
```

### Complex Functions

#### Static Typing

You can expand upon functions to use static typing rules like with variables earlier.

You can statically type arguments the same we statically type variables, by following the
identifier with a hash symbol and then the type name.

To statically type the return value, insert an equals sign and then the type name before the
body of the function.

```jpizza
fn add<x#num, y#num> = num {
    return x + y;
}

<> Statically types x and y to be numbers.
<> = num makes the return value a number.
```

#### Default Arguments

We can do even more with arguments after this too. We can add default values to arguments,
so if they are left unspecified the default arguments are substituted in. After you start
declaring default arguments however, each following argument must have a default value.

To add a default value, simply follow the argument with an equals sign and then the default
value.

```jpizza
fn add<x#num, y#num = 1> = num {
    return x + y;
}

<> Now y has a default value of 1.

println(add(5));
<> Prints 6, since 1 is substituted in for the missing y argument.

println(add(7, 2));
<> Prints 9, since y is accounted for.
```

#### Asynchronous Functions

By adding the keyword '**async**' after the **fn** keyword, we can make the function asynchronous.
This means that the program doesn't wait for the function to finish before continuing, the function
simply runs in the background.

```jpizza
import time;

fn async printTen<msg> {
  for (i -> 0:10) {
    println(msg);
    time::halt(500); <> Pauses for 500ms.
  }
}

printTen("This is asynchronous!");
printTen("This is also asynchronous!");

<> Both messages are printed ten times simultaneously.
```

## Enumerators

### What is an Enumerator?

Enumerators are values that consist of predefined constants.
This essentialy means that we can define an enumerator with a bunch of keywords we want
to use in our pgoram later on without having to give them values. JPizaz is special, where enums
are their own type compared to most languages giving them integer values. Enums comparisons are only
true when compared to enums of the same parent and name.

### How to Make an Enumerator

You can define an enumerator using the '**enum**' keyword followed by curly braces, (`{}`).
Inside the curly braces should be each keyword followed by a comma, including the last one.

To access enums from their parent, use the parent followed by the double colon operator, (`::`),
and then the enum name.

```jpizza
enum PizzaToppings {
  sausage,
  pineapple,
  pepperoni,
};

var favorite => PizzaToppings::sausage;
if (favorite == PizzaToppings::pineapple) {
  println("You are mentally unstable.");
}
```

## Structures

### What are Structures?

Structures, or structs for short, are an easy way to create custom data 
structures. You can use structs to easily store several pieces of data all 
with unique names and access them later.

### How to Make a Structure

You can define a structure similar to an enumerator. First, start with the keyword
'**struct**', followed by the name of your data structure type.

After this comes the body. Open with curly braces, (`{}`), and list each attribute
of the struct with commas in between. After closing with a curly bracket and
a semicolon, your struct is complete.

```jpizza
struct Vector3 {
  x,
  y,
  z
};

<> Creates a new struct Vector3 with the attributes
<> x, y, and z.
```

### Using Structures

You can create new instances of structures by calling them like a function and passing
each attribute in. The order in which you pass the attributes in should follow
the order of definition.

You can access data from a struct instance with the double colon operator, (`::`), followed
by the attribute name.

```jpizza
struct Message {
  username,
  contents
};

var msg => Message("John Doe", "Hello world!");
<> Creates a new message instance.

println(msg::contents);
<> Gets the contents of the message and 
<> prints them out.
```

## Objects

*This chapter assumes you have read the **Functions** chapter.*

### What are Objects?

Objects are essentially custom types that you can create. You can give them custom attributes
and methods that they can execute, along with custom properties like handling for addition and
other operations.

### How to Make an Object

Due to this being JPizza, objects are defined using the '**recipe**' keyword, followed by the
name of the object and curly braces, (`{}`). Inside the curly braces will be all of our code.

#### Attributes

##### How to Declare Attributes

First, object attributes must be listed as the first line of code.
The name of each attribute must be seperated by a comma, and the line should end in a semicolon.

```jpizza
recipe Pizza {
  topping, breading;
  <> Declares the attributes topping and breading.
};
```

##### How to Access and Set Attributes

Attributes can only be accessed using the '**this**' keyword or by using the '**attr**' keyword.

When using the **this** keyword, follow it with the double colon operator, (`::`), followed by
the attribute name.

When using the **attr** keyword, follow it with the name of the attribute. If you want to assign
a value to an attribute, follow the name with an arrow and then the value you want to assign to it.

#### Constructor

##### What is a Constructor?

The constructor is a function that is called when you make a new instance of the object.
The constructor can accept arguments, or it can just run default code.

##### How to Make a Constructor

To define a constructor, use the '**ingredients**' keyword. Then follow it with arguments
similar to a function. Angle brackets with the parameters inside, omitt if there aren't any.

Finally, use curly braces, (`{}`), with your constructor code inside.

```jpizza
recipe Pizza {
  topping, breading;
  <> Declares the attributes topping and breading.
  
  ingredients<t, b> {
    attr topping => t;
    attr breading => b;
    
    <> Creates a constructor that takes in t and b, 
    <> then assigns toppings to t and breading to b.
  }
  
};
```

##### Complex Constructors

Constructors support the same static typing and default arguments as functions,
however, they do not return a value.

#### Methods

##### What is a Method?

Methods are functions that the object can execute from its current instance.
Similar to functions, they can accept arguments, and they 
can use both brace and arrow form, but they cannot be anonymous.

##### How to Make a Method

To define a method, use the '**method**' keyword, followed by the arguments and the body.

```jpizza
recipe Pizza {
  ... <> Previous code.
  method details {
    println("I am a pizza with " + this::breading
              + "breading and " + this::topping + ".");
  }
}
```

##### Complex Methods

Methods support static typing, asynchronous execution, and default arguments
just like functions.

However, methods have another special trait, which is the '**bin**' keyword.
**Bin** is short for built-in, and allows you to override built-in methods, like
addition.

To make a method a **bin** method, simply write the **bin** keyword after the **method**
keyword.

```jpizza
recipe Number {
  value;
  ingredients<val> {
    attr value => val;
  }
  
  method bin add<o> -> this::value + o::value
  <> Overrides the built-in addition function.
  
};
```


### Using Objects

To create a new instance of an object, you can call it like a function. Any arguments you pass in
are passed into the constructor.

You can access methods and attributes of the instance using the double colon operator, (`::`).
On the left of the operator should be the instance, and the attribute/method name should be on the right.

```jpizza
recipe Pizza {
  ...
};

var myPizza => Pizza("sausage", "pretzel");
<> Creates a new pizza, passing "sausage" and "pretzel" into the constructor.

myPizza::details();
<> Calls the details function of the pizza instance.
```

## Packages
A useful feature of Pizza is the import and packages system.

You can import scripts with the '**import**' keyword followed by the script name,
(*minus the file extension*). This allows you to access all the script's attributes
like its functions, variables, classes, and other components. This can be done
similarly to accessing class attributes, using the double colon operator, (`::`).

You can import both local and global scripts. To make a script global, make a new folder
under `C:\DP\modules\ ` with the same name as the script, (*minus the file extension*), 
then put the script in there.

```jpizza
<> otherScript.devp

fn sayHello -> println("Hello another world!");
```

```jpizza
<> mainScript.devp

import otherScript;

otherScript::sayHello();
<> Prints "Hello another world!".
```


## Headers

Your code functionality can be modified using header statements. Header statements start with
a hash symbol, followed by the header name. If the header requires arguments, seperate each
argument with a space.

An example of a header is the **func** header, which runs a function as a main function after
the script is executed. This is useful if you want a main function that only runs when the
script is executed, and not when it's imported or interacted with in other ways.

This header takes in one argument, the name of the main function. The main function must take in
one argument, which is the command line arguments.

```jpizza
#func myMainFunction;

fn myMainFunction<args#list> {
  println("Hello world!");
}

<> At the end of the script, myMainFunction is called.
```

Some headers are context based, meaning if you put them somewhere like inside a function,
it will only affect how the function treats the code, but it won't affect the code globally.

This is useful for headers like **memoize**, which caches function inputs and instantly
returns the value instead of running the function code if the same inputs are ever given to
a function.


