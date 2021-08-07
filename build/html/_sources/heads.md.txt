
# Headers

## Execution

- `func <functionName>` : If the program is being directly executed, at the end of the script it
will run the function specified and pass in a list of command line arguments as a parameter.
- `object <recipeName>` : If the program is being directly executed, at the end of the script it
will create a new instance of the object specified and run the main method passing in a list of
command line arguments as a parameter.

## Optimization

- `memoize` : Caches function calls so when functions are called with arguments that have been
called before, it will automatically return the value instead of running the function.
