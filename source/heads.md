
# Headers

## Execution

- `func <functionName>` : If the program is being directly executed, at the end of the script it
will run the function specified and pass in a list of command line arguments as a parameter.
- `object <recipeName>` : If the program is being directly executed, at the end of the script it
will call the static method named main of the given class and pass in a list of command line arguments as a parameter.

## Optimization

- `memoize` : Caches function calls so when functions are called with arguments that have been
called before, it will automatically return the value instead of running the function.

## Exports

- `export <args>` : Allows only the specified arguments to be imported into other scripts.
- `export_to <target>` : Changes what types of files can import the script.
    - `all` : All files can import the script.
    - `package` : Only scripts in the same package can import the script.
    - `none` : No files can import the script.
- `package <packageName>` : Changes the package the script is in.
