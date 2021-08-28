
# Native Functions

## In / Out
- `print<value>` : Prints the given value.
- `println<value>` : Prints the given value along with a new line.
- `printback<value>` : Prints and returns the given value.
- `field<prompt>` : Prompts the user with the given text and waits for an input.
- `nfield<prompt>` : Prompts the user with the given text and waits for a numerical input.
- `clear` : Clears the console
- `sim<text>` : Simulates the text as code and returns the output.
- `run<filepath>` : Runs the given file.
  
## Type Checking

- `isNumber<value>` : Returns if the given value is a number.
- `isString<value>` : Returns if the given value is a string.
- `isList<value>` : Returns if the given value is a list.
- `isFunction<value>` : Returns if the given value is a function.
- `isNull<value>` : Returns if the given value is null.
- `isBool<value>` : Returns if the given value is boolean.
- `type<value>` : Returns the type of the given value as a string.
- `enumProps<inst, prop>` : Returns if the given instance is an instance of the provided enum property.

## List Modifiers

- `append<list, value>` : Appends the given value to the list.
- `pop<list, index>` : Removes the item at the given index from the list.
- `extend<list, list>` : Returns the concatenation of the two lists.
- `insert<list, item, index>` : Inserts the given item at the given index of the list.
- `setIndex<list, item, index>` : Sets the given index to the given item of the list.
- `size<list>` : Returns the size of the given list.
- `foreach<list, func>` : Applies the given function to each element of the list.
- `choose<list>` : Chooses a random item from the list.
- `contains<list, value>` : Returns true if the list contains the value.
- `sublist<list, start, end>` : Returns the sublist between the start and end indices.
- `join<str, list>` : Returns a string of each item in the list seperated by `str`, for example: `join(" ", ["Hello,", "World!"]) -> "Hello, World!"`

## Dictionary Modifiers

- `get<dict, key>` : Returns the value of a key in the dictionary.
- `set<dict, key, value>` : Sets the value of a key in the dictionary.
- `delete<dict, key>` : Removes a key from the dictionary.
- `contains<dict, value>` : Returns true if the dictionary contains the value.

## Numerical Functions

- `pi` : π.
- `euler`: *e*.
- `log<value, base>` : Gets the logarithm of the provided value using the base.
- `round<value>` : Rounds the value to the nearest whole number.
- `floor<value>` : Rounds the value down.
- `ceil<value>` : Rounds the value up.
- `abs<value>` : Gets the absolute value of a number.
- `random` : Returns a random number between 0 and 1.
- `randint<min, max>` : Returns a random number between the min and max.
- `floating<value>` : Returns if the number is a floating point number.
- `max<a, b>` : Returns the maximum value between `a` and `b`.
- `min<a, b>` : Returns the minimum value between `a` and `b`.
- `sin<x>` : Returns the sine of `x`.
- `cos<x>` : Returns the cosine of `x`.
- `tan<x>` : Returns the tangent of `x`.
- `arcsin<x>` : Returns the inverse sin of `x`.
- `arccos<x>` : Returns the inverse cosine of `x`.
- `arctan<x>` : Returns the inverse tangent of `x`.
- `arctan2<y, x>` : Returns the inverse tangent of `y` and `x`.

## Type Conversions

- `str<value>` : Converts the given value to a string.
- `num<value>` : Converts the given value to a number.
- `bool<value>` : Converts the given value to boolean.
- `list<value>` : Converts the given value to a list.
- `dict<value>` : Converts the given value to a dictionary.
- `func<value>` : Converts the given value to a function... for some reason.
- `byter<value>` : Converts a list of numbers into a byte array.

## String Modifiers

- `split<string, delimiter>` : Splits the string into a list every time the delimiter is found.
- `contains<string, value>` : Returns true if the string contains the value.
- `strUpper<string>` : Returns the string with all letters uppercase.
- `strLower<string>` : Returns the string with all letters lowercase.
- `strShift<string>` : Returns the string with all characters in the form they would be if you were to hold shift.
- `strUnshift<string>` : Returns the string with all characters in their form if you were to not hold shift. (Inverse of `strShift`)
- `substr<str, start, end>` : Returns the substring between the start and end indices.

## Object Functions

- `getattr<instance, attribute>` : Uses the vanilla get method to access the instances value.
- `hasattr<instance, attribute>` : Returns true if the instance has the attribute in question.

## Internal

- `_version_` : Returns the version number of your JPizza installation.
