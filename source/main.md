
# Main Documentation

## Comments

Comments are statements that the programming language ignores.
You can declare comments in JPizza using two angle brackets facing away from each other.

You can also make multiline comments using two left facing angle brackets as the opening and closing.

```jpizza
<> This is a comment.

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
- `x=` (*where x is any binary operation above*) - Assigns the left operand, assuming it is a variable, to the result of the binary operation `x`.
- `:` - Returns the left value unless it is `null` or causes an error, in which case it returns the right value. If the right value causes an error, it returns `null`.

### Unary Operations

Unary Operations only take in one operand.

- `x++` - Increments `x` and assigns the value to `x`, assuming it is a variable.
- `x--` - Decrements `x` and assigns the value to `x`, assuming it is a variable.
- `--x` - Returns the decremented value of `x`.
- `++x` - Returns the incremented value of `x`.
- `-x` - Gets the negative value of `x`.
- `!x` - Inverts `x`.
- `@x` - Converts `x` into a byte array.
- `$x` - Turns byte array `x` into an object.
- `~x` - Gets the binary complement of integer `x`.

### Conditional Operations

- `&` - Checks if both the left operand, and the right operand are true.
- `|` - Checks if either the left operand, or the right operand is true.
- `>` - Checks if the left operand is greater than the right operand.
- `>=` - Checks if the left operand is greater than or equal to the right operand.
- `<` - Checks if the left operand is less than the right operand.
- `<=` - Checks if the left operand is less than or equal to the right operand.
- `==` - Checks if the left operand is equal to the right operand.
- `!=` - Checks if the left operand is not equal to the right operand.

### Bit Operations

- `~&` - Gets the bitwise and of both operands.
- `~|` - Gets the bitwise or of both operands.
- `~^` - Gets the bitwise xor of both operands.
- `<~` - Bit shifts the left operand by the right operand.
- `~~` - Performs an unsigned bit shift on the left operand by the right operand.
- `~>` - Performs a signed bit shift on the left operand by the right operand.

## Advanced Numbers

JPizza has some additional number properties.

### Hex Numbers

You can create a hex number by typing `0x` followed by your hex number. These have the type of `hex`, and are represented as `0xHEXNUMBER` when printed. Adding a hex number to a normal number results in a normal number, but adding a normal number to a hex number results in a hex number.

`1 + 0x1 = 2`
`0x1 + 1 = 0x2`

### Algebraic Multiplication

Similar to algebra, you can enter commands such as `3x` as a shorthand for `3 * x`. However, you cannot do this with two variables, only a variable in a number. Attempting to do `xy` results in an error, since it treats `xy` as one word.

`var x => 4;`
`3x -> 12`

## Variable Assignment

Variables are defined using the keywords '**var**' and '**bake**'.

**Bake** permanently sets a variables value, to where it cannot be changed. You can also use **const** as an alternative to this keyword.

After variables are defined, they can be set with the **var** keyword omitted. 
This will set the variable of the same name in the most recent scope.

```jpizza
var x => 3;
bake y => "Hello!"; <> const y => "Hello!"; works also
x => 4;
y => "Goodbye!"; <> Throws an error since y is a baked variable.
```

You can declare multiple variables as null in the same statement by seperating each by a comma.

```jpizza
var x, y, z;
<> Declares x, y, and z! All are set to null.

x => 1; y => 2; z => 3;
<> Works!
```

If you want to remove a variable from the scope, you can use the `free` keyword followed by the variable name.

```jpizza
var x => 2;
println(x); <> 2

free x;
println(x); <> Error!
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
you can statically type them using a colon followed by the variable type.

```jpizza
var x: num => 4;
<> Sets the type of variable x to be a number.

x => 8; <> Ok!
x => "Hello!"; <> Error!
```

To statically type variables quickly, you can use the **let** keyword, by doing `let x => value;`. This will automatically statically type `x` to the type of `value`.

```jpizza
let x => 4;
<> Sets x to 4 and statically types x to the type of 4, which is a number.

x => 8; <> Ok!
x => "Hello!"; <> Error!
```

One final special feature of variables is range limitations. In JPizza, you can use square brackets following a variable name to limit the range
that a numeric value may lie in under that variable. By default, the value you enter will be the maximum, and the minimum will be set to 0. To add a
custom minimum along with the maximum, you can have the minimum, followed by a pipe, (`|`), and then the maximum.

```jpizza
var sbyte [ -127 | 127 ] => 56;
<> Limits the variable sbyte to a range of -127 <= n <= 127.
var usbyte [ 255 ] => 12;
<> Limits the variable usbyte to a range of 0 <= n <= 255.

<> Assigning either variable to a non-numeric or a number outside of the range causes a runtime error!
```

## Format Strings

Format strings give you the ability to directly inline variables and expressions into strings! To do this, create a string using backticks, (`` ` ``), and inline
any variables inside of brackets prefixed with a dollar sign. To escape that, you can prefix the dollar sign with an exclamation mark.

```jpizza
var x => 4;

println(`The value of x is ${x}`); <> Prints "The value of x is 4".
println(`To write ${x} you can do !${x}`); <> Prints "To write 4 you can do ${x}".
```

## Lists

Lists are, simply put, a list or array of values.

Lists are defined using square brackets. Inside the brackets are each element,
seperated by a comma.

List elements can be accessed by enclosing the index you want to access in square brackets
following the list.

If you use a negative number to access a list index, it counts backwards.

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
Match statements also have the ability to use the pattern matching feature, which will be elaborated on momentarily.

To declare a match statement, start with the '**match**' keyword followed by the value you want to
compare in parentheses. Then follow it with curly braces, (`{}`).

Inside the braces are the cases. To declare a new case, start with the keyword '**case**' followed by
the value you want to check. Follow the value with a temporary assignment arrow, (`->`) followed by the value you
want to return and then a semicolon.

To add a default case, you can use the '**default**' keyword followed by an arrow, and the value you want to
return.

```jpizza
println(match (4) {
    case 2 -> 4;
    case 4 -> 8;
    case 8 -> 12;
    
    default -> 0;
});

<> Prints the matching value, which is 8 in this case.
```

You can also use pattern matching, which allows you to declare a special statement called a pattern and use that to extract or test specific attributes against an object. The general syntax for pattern matching is the object name followed by parenthesis. Inside of the parenthesis should be the attribute name followed by a colon and then the expected value, each separated by a comma. You can make the expected value a variable that does not exist, and it will instead assign the value of the attribute to that variable if the rest of the pattern matches. You can also omit the colon and expected value and it will automatically set the expected value to be a variable that is the same name as the attribute.

```jpizza
class Box {
  pub value;
  ingredients<x> {
    value => x;
  }
}

var example => Box(123);
match (example) {
  Box(value: 456) -> println("Is Box(456)");
  <> Tests if its a Box where the attribute 'value' is 456.

  Box(value: x) -> println(`Is Box(${x}`);
  <> Tests if its a Box, and assigns the attribute 'value' to the variable x.

  Box(value) -> println(`Is Box(${x})`);
  <> Tests if its a Box, and assigns the attribute 'value' to the variable value.
  <> Same thing as Box(value: value)
};
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

**NOTE:** *Anonymous functions must be followed by a semicolon, even if you're using curly braces, (`{}`).*

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

You can also return the last line of code automatically by omitting the semicolon on the last line.

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

You can also spread a list of arguments out over a function using the spread operator (`..`) followed by the list.

```jpizza
println(add(..[3, 4])); <> This is the same as add(3, 4), it spreads out the values into the arguments.
```

### Complex Functions

#### Static Typing

You can expand upon functions to use static typing rules like with variables earlier.

You can statically type arguments the same we statically type variables, by following the
identifier with a colon and then the type name.

To statically type the return value, insert either the keyword '**yields**' or a colon and then the type name before the
body of the function.

```jpizza
fn add<x: num, y: num> yields num {
    return x + y;
}

<> Statically types x and y to be numbers.
<> yields num makes the return value a number.
```

#### Generic Typing

Along with static typing, you can use generic typing. Simply follow the arguments with parenthesis containing the generic type names. When calling the function, pass in the types inside angle brackets after the arguments.

```jpizza
fn myGeneric<x: T>(T) -> println(`${x} has a generic type of ${T}`);

myGeneric(2)<num>;

<<
Console Output:
"2 has a generic type of num"
<<
```

Generic types can also be inferred. If the type has an argument that uses that type and the type is omitted, it will automatically infer that the type will be the same as the variable. This allows you to simplify the above call to:

```jpizza
myGeneric(2); 
<> Since x is of type T, and the 
<> provided x has a type of num,
<> it infers that T is num
```

#### Default Arguments

We can do even more with arguments after this too. We can add default values to arguments,
so if they are left unspecified the default arguments are substituted in. After you start
declaring default arguments however, each following argument must have a default value.

To add a default value, simply follow the argument with an equals sign and then the default
value.

```jpizza
fn add<x: num, y: num = 1> yields num {
    return x + y;
}

<> Now y has a default value of 1.

println(add(5));
<> Prints 6, since 1 is substituted in for the missing y argument.

println(add(7, 2));
<> Prints 9, since y is accounted for.
```

#### Iterative Arguments

You can get any extra arguments passed in as a list by putting `..` followed by the name you want it to be assigned to at the end of your arguments. Following this with any more argument names will cause an error.

```jpizza
fn iterativePrint<..messages> {
  <> Iterates through each argument and prints it
  for (i <- messages) {
    print(i);
  }
}

iterativePrint("a", "b", "c");
<> Passes in ["a", "b", "c"] to the function as the variable 'messages'
<> Ends up printing abc
```

#### Keyword Arguments

You can get a dictionary of specifically named arguments by putting a backslash after your last argument and then the name of what you want the dictionary to be passed in as. To give a function specifically named arguments, follow your last argument with a backslash when calling it. After the backslash give it all of your named arguments in the format `name: value`, each seperated by a comma.

```jpizza
fn printNamed<\ dict> {
  <> Iterates through every pair and prints it
  for (key <- list(dict)) {
    println(`${key}: ${dict[key]}`);
  }
}

printNamed(\ a: "b", c: 4, hello: "world");
<<
Passes {"a": "b", "c": 4, "hello": "world"} in to printNamed as dict
Prints out:
a: b
c: 4
hello: world
<<
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

#### Decorators

Similar to other languages, JPizza suppports decorators. Decorators are functions that are called before the function they are decorating. They can be used to modify the behavior of the function they are decorating.

```jpizza
fn myDecorator<func> -> fn <x> {
  println(x);
  return func(x) + 1;
}

/myDecorator/
fn coolFunc<x> -> 2x;

println(coolFunc(3));

<<
Console Output:
3
7
<<
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
  Sausage,
  Pineapple,
  Pepperoni,
}

var favorite => PizzaToppings::Sausage;
if (favorite == PizzaToppings::Pineapple) {
  println("You are mentally unstable.");
}
```

### Public Enumerators

You can also follow the **enum** keyword with **pub** to make each child publicly available.

```jpizza
enum pub PizzaToppings {
  Sausage,
  Pineapple,
  Pepperoni,
}

var favorite => Sausage; <> Works!
if (favorite == Pineapple) {
  println("You are mentally unstable.");
}
```

### Complex Enumerators

Along with enums, you can add properties to each child. Adding properties essentially allows you to construct a unique instance of each child except it has additional
properties that can be accessed. You can add properties to children by adding curly braces after the child name, and put each property seperated by a comma inside them. You can statically type each property by following it with a colon and then the type. You can then instance the child by calling it like a function.

```jpizza
enum Message {
  Quit,
  Move { x: num, y: num },
  Write { text: any },
  ChangeColor { r: num, g: num, b: num },
}

var write => Message::Write("mytext");
println(write::text); <> Prints "mytext"
```

To statically type enums further, you can use generic types with enum properties.

```jpizza
enum Option {
  Some(T){ val: T },
  None
}

var x => Some(13);
prinln(type(x)); <> Prints Option(num)
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
}

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
}

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

Due to this being JPizza, objects are defined using the '**class**' keyword, followed by the
name of the object and curly braces, (`{}`). Inside the curly braces will be all of our code.

*Note: the original keyword for objects was **recipe** to fit the Pizza theme, but it was changed to **class** to be more standardized. You can also use **obj**!*

#### Attributes

##### How to Declare Attributes

There are many ways to declare attributes, but attributes must be declared otherwise they will not stay inside the object.

The simplest way is to simply list off the attribute names, each seperated by a comma. You can also list each off one at a time. To assign a default value to an attribute, you can have the attribute name followed by an arrow and then the value, like variable assignment. To statically type an attribute, you can follow the name with a colon and then the type. 

Finally, you can add modifiers to attributes. You can use the `pub` keyword to make them public, meaning they can be accessed outside of the object, which is the default. Prefixing it with `prv` makes it private, so it can only be accessed internally. The `static` modifier makes it so that it can be accessed from the object directly, and not from an instance.

```jpizza
class Pizza {
  topping, breading;

  topping;
  breading;

  topping: String => "...";
  breading: String => "...";

  pub topping;
  prv breading => "Shh!";

  static topping => "topping being worked on...";
  static breading => "breading in progress...";
  <> Declares the attributes topping and breading in several different ways to show off the different methods.
}
```

##### How to Access and Set Attributes

Attributes can be accessed similar to variables, by simply referencing the associated name. However, if there is a variable in scope of the same name, there are alternative methods. You can use the `this` keyword followed by the double colon operator, (`::`), and then the identifier. You can also use the **attr** keyword followed by the identifier.

To set attributes, you can set them similar to variables, by following the identifier with an arrow and a value, however if there is a varible in scope of the same name, you can use alternative methods. You can use the **attr** keyword followed by the identifier, an arrow, and a value.

#### Constructor

##### What is a Constructor?

The constructor is a function that is called when you make a new instance of the object.
The constructor can accept arguments, or it can just run default code.

##### How to Make a Constructor

To define a constructor, use the '**ingredients**' keyword. Then follow it with arguments
similar to a function. Angle brackets with the parameters inside, omitt if there aren't any.

Finally, use curly braces, (`{}`), with your constructor code inside.

```jpizza
class Pizza {
  topping, breading;
  <> Declares the attributes topping and breading.
  
  ingredients<t, b> {
    attr topping => t;
    attr breading => b;
    
    <> Creates a constructor that takes in t and b, 
    <> then assigns toppings to t and breading to b.
  }
  
}
```

##### Complex Constructors

Constructors support the same complex features as functions, but constructors do not return a value.

You can also use generic typing on constructors the same as you would functions. To pass in generic types, you would simply append the generic types to the end of the class call in angle brackets.

`var cls => GenericClass(args)<types>;`

#### Methods

##### What is a Method?

Methods are functions that the object can execute from its current instance.
Similar to functions, they can accept arguments, and they 
can use both brace and arrow form, but they cannot be anonymous.

##### How to Make a Method

To define a method, use the '**mthd**' keyword, followed by the arguments and the body.
*Note: you can also use **md** or **method** instead of **mthd**.*

```jpizza
class Pizza {
  ... <> Previous code.
  mthd details {
    println("I am a pizza with " + this::breading
              + "breading and " + this::topping + ".");
  }
}
```

##### Complex Methods

Methods support static typing, asynchronous execution, generic typing, default arguments, and everything else functions have.

However, methods have another special trait, which is the '**bin**' keyword.
**Bin** is short for built-in, and allows you to override built-in methods, like
addition.

To make a method a **bin** method, simply write the **bin** keyword after the **mthd**
keyword.

```jpizza
class Number {
  value;
  ingredients<val> {
    attr value => val;
  }
  
  mthd bin add<o> -> this::value + o::value
  <> Overrides the built-in addition function.

}
```

Methods also share the same modifiers as attributes, such as `pub`, `prv`, and `static`. By default, methods are public, but if you use a lot of different publicities, specifying `pub` may help.

To apply these modifiers, simply write them after the **mthd** keyword.

```jpizza
class MyCoolMethods {
  mthd pub publicMethod {
    println("I am public!");
  }

  mthd prv privateMethod {
    println("I am private! Wait, how did you call me??");
  }

  mthd static staticMethod {
    println("You can call me anywhere!");
  }
}
```

### Using Objects

To create a new instance of an object, you can call it like a function. Any arguments you pass in
are passed into the constructor.

You can access methods and attributes of the instance using the double colon operator, (`::`).
On the left of the operator should be the instance, and the attribute/method name should be on the right.

```jpizza
class Pizza {
  ...
}

var myPizza => Pizza("sausage", "pretzel");
<> Creates a new pizza, passing "sausage" and "pretzel" into the constructor.

myPizza::details();
<> Calls the details function of the pizza instance.
```

### Complex Objects

Objects have some special properties that make things easier.

#### Inheritance

Inheritance simply means that we can give an object a parent object, and it "inherits" all its attributes, methods, and constructor properties. These can be 
overwritten simply by defining it in the object, but it's useful if you have several objects all with the same methods. You can just make a parent object!

To give an object a parent, you can use the temporary assignment arrow, (`->`), after the object name and follow it with the name of the parent object.

```jpizza
class Parent {
  inheritedAttribute;
  ingredients<x> {
    attr inheritedAttribute => x;
  }

  mthd inheritedFunction<y> -> this::inheritedAttribute + y

}

class Child -> Parent {
  ingredients<x> {
    attr inheritedAttribute => x + 2;
    <> Overrides the default constructor and replaces it with this one, which adds 2 to x before assigning it to v.
  }
}

println(Parent(5)::inheritedFunction(2));
<> Prints 7.

println(Child(5)::inheritedFunction(2));
<> Prints 9, since 2 is added to x in the overridden constructor.
```

## Scopes
### What is a Scope?

A scope can be thought of like a bubble that contains local variables, but once you exit the scope all the variables are lost. When you call a function, the code in the function is in a new scope, but then it exits the scope once the call finishes. This is why you can't access variables initialized inside the function.

### How to Make a New Scope

You can create a scope using the **scope** keyword followed by the code you want to run inside curly braces. You can also name scopes by putting the name inside square brackets after **scope**. This allows for a cleaner traceback in runtime errors.

```jpizza
var x => 5;

scope [my_cool_scope] {
  var y => 15;
  println(x + y);
}
<> The variable y can no longer be used!

scope {
  println("Unnamed scope!");
}
```

### Returning Values from Scopes

You can return values from scopes just like in functions, and you can then use that value in your code.

```jpizza
var x => scope {
  var y => 9 + 10;
  return y;
} <> Assigns x to the return value of the scope, 21 in this case.
```

## Packages
### Scripts
A useful feature of Pizza is the import and packages system.

You can import scripts with the '**import**' keyword followed by the script name,
(*minus the file extension*). This allows you to access all the script's attributes
like its functions, variables, classes, and other components. This can be done
similarly to accessing class attributes, using the double colon operator, (`::`).

To import the script under a different name, you can use the **as** keyword followed by the preferred name.

You can import both local and global scripts. To make a script global, make a new folder
under `~/.jpizza/modules/` with the same name as the script, (*minus the file extension*), 
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

import otherScript as o_script;
<> Imports otherScript with the name o_script.

o_script::sayHello();
<> Also prints "Hello another world!".
```

### Extensions
You can extend JPizza with extensions written in Java that function as packs of new libraries. This can be done with the **extend** keyword followed by the extension name (*minus the file extension*). This gives you access to all of the libraries the extension has, which can then be imported.

You can extend both local and global extensions. To make an extension global, make a new folder under `~/.jpizza/extensions/` with the same name as the extension, (*minus the file extension*), and then put the jar in there.

```jpizza
extend MyCoolExtension;
import mycoollibrary;

mycoollibrary::myCoolFunction();
<> Runs myCoolFunction
```

### Destructuring
You can use a feature known as destructuring to extract certain methods from imports and use them in the global scope. This can generally be applied to any data object such as classes and structs, but is most useful in the case of imports.

To destructure an object, simply do **var** followed by each attribute name separated by spaces inside of curly braces. Then follow that with an assignment arrow and the expression you want to destructure, in this case an import.

To destructure everything from an import, you can use a star (`*`) inside curly braces instead of names.

```jpizza
<> otherScript.devp

fn sayHello -> println("Hello another world!");

fn sayGoodbye -> println("Goodbye another world!");
```

```jpizza
<> mainScript.devp

var { sayHello } => import otherScript;
<> Moves sayHello from otherScript into the current scope.

sayHello();
<> Prints "Hello another world!".

var { * } => import otherScript;
<> Moves all functions from otherScript into the current scope.

sayGoodbye();
<> Prints "Goodbye another world!".
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

fn myMainFunction<args: list> {
  println("Hello world!");
}

<> At the end of the script, myMainFunction is called.
```

Some headers are context based, meaning if you put them somewhere like inside a function,
it will only affect how the function treats the code, but it won't affect the code globally.

This is useful for headers like **memoize**, which caches function inputs and instantly
returns the value instead of running the function code if the same inputs are ever given to
a function.



## Error Handling

Error handling in JPizza is similar to a language called Rust. We can make functions return a **Resolve** object which contains an error and a value.
If the function failed, the object will only contain the error, and trying to access the value will result in another error.
You can check if a resolve is error free with the `ok` function.

### How to Get a Resolve Object

To get a **Resolve** object, we need to make our function a catcher function. We can do this by append a pair of brackets `[]` to the end of a functions arguments.
If no arguments, then name, no name then keyword. To create a demo function, we're going to use the '**throw**' keyword. This allows us to create a custom error by
"throwing" the statement following it as an error message.

```jpizza
fn myIffyFunction[] {
  var r => random();

  if (r > 0.5)
    throw 'Fail!!!';

  return r;
}

<> This function will fail 50% of the time and return a random number the other 50%.
```

*Note about 'throw': If you provide two strings separated by a comma, it will use the first string as the error type and the second as the details.*

### Handling Resolves

There are several special functions that we can use to handle **Resolves**. 

The first function is `ok`. Doing `ok(res)` will return a bool determining whether the object is error free. 

If our object is error free, we can safely call `resolve(res)`, which will return the value of the **Resolve**. Beware! If there is an error and
no value, this will throw an error. Always do some form of `if (ok(res))` before.

The next function is `catch(res)`, which will return the error type and error message of the object as a list. We can then handle the error as we please.

If we want to throw the error anyway, we can call `fail(res)`, which throws the error stored.

```jpizza
<> Assume the "myIffyFunction" from earlier is defined here.

var res => myIffyFunction();
<> ^^ Assigns the result to res.
<> VV Checks if the result is error free.
if (ok(res)) {
  println(resolve(res));
  <> Prints the random number returned.

} else {
  println("Encountered error: " + catch(res));
  <> Prints "Encountered error: [<Error Name>, <Error Message>]".

}

```

## Intended Errors

### Throw

Like mentioned in the chapter 'Error Handling', we can use **throw** to throw a custom error. Throw can be used in two forms, we can provide a single string that will be used as the error message, or two strings that will be the error name and error message. If no error name is provided, it will default to "Thrown".

```jpizza
throw "Custom Error Type", "You suck!!";
throw "You suck, generally!!";
```

### Assertion

Assertion allows you to throw errors if a given condition is false. Assertions can be defined by simply using the **assert** keyword followed by a condition.

```jpizza
assert "abc" == "abc"; <> Ok!
assert  123  ==  456 ; <> Uh oh! Assertion Error is brought up!
```

## References

### What is a Reference?

References work like boxes that contain a value. When a reference is copied or passed somewhere, it still contains the same value. References allow you to mutate the value inside, and it modifies the value across all references that use it.

### How to Make a Reference

You can make a reference using an ampersand (`&`) followed by the expression. You can dereference something, or get the value the reference is pointing to, by using a star (`*`).

Assignment operations like `=>`, `+=`, `++`, and more are implemented on references, and directly mutate the value. This allows you to do things like edit items at list indices directly by making a list of references.

```jpizza

var lis => [&1, &2, &3, &4, &5];

lis[0] => 23;
lis[1]++;
lis[2] -= 15;

println(lis);
<> Prints [23, 3, -12, 4, 5].

println(3 + *lis[0]);
<> Prints 26.
```
