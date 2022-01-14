
# Native Functions

## In / Out
- `print<value>` : Prints the given value.
- `println<value>` : Prints the given value along with a new line.
- `printback<value>` : Prints and returns the given value.
- `field<prompt>` : Prompts the user with the given text and waits for an input.
- `nfield<prompt>` : Prompts the user with the given text and waits for a numerical input.
- `clear` : Clears the console
- `sim<text>` : Simulates the text as code.
- `run<filepath>` : Runs the given file.
  
## Type Checking

- `isNumber<value>` : Returns if the given value is a number.
- `isString<value>` : Returns if the given value is a string.
- `isList<value>` : Returns if the given value is a list.
- `isFunction<value>` : Returns if the given value is a function.
- `isBoolean<value>` : Returns if the given value is boolean.
- `type<value>` : Returns the type of the given value as a string.

## List Modifiers

- `append<list, value>` : Appends the given value to the list.
- `remove<list, value>` : Removes the given value from the list.
- `pop<list, index>` : Removes the item at the given index from the list.
- `extend<list, list>` : Returns the concatenation of the two lists.
- `insert<list, item, index>` : Inserts the given item at the given index of the list.
- `setIndex<list, item, index>` : Sets the given index to the given item of the list.
- `size<list>` : Returns the size of the given list.
- `choose<list>` : Chooses a random item from the list.
- `contains<list, value>` : Returns true if the list contains the value.
- `sublist<list, start, end>` : Returns the sublist between the start and end indices.
- `join<str, list>` : Returns a string of each item in the list seperated by `str`, for example: `join(" ", ["Hello,", "World!"]) -> "Hello, World!"`
- `indexOf<list, item>` : Returns the index of the item in the list. Returns -1 if the item is not in the list.

## Dictionary Modifiers

- `get<dict, key>` : Returns the value of a key in the dictionary.
- `set<dict, key, value>` : Sets the value of a key in the dictionary.
- `overset<dict, key, value>` : Replaces the value of a key in the dictionary if it exists.
- `delete<dict, key>` : Removes a key from the dictionary.
- `contains<dict, value>` : Returns true if the dictionary contains the value.

## Numerical Functions

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
- `doubleStr<number, precision>` : Returns the number as a string with the given decimal precision.

## Type Conversions

- `str<value>` : Converts the given value to a string.
- `num<value>` : Converts the given value to a number.
- `bool<value>` : Converts the given value to boolean.
- `list<value>` : Converts the given value to a list.
- `dict<value>` : Converts the given value to a dictionary.
- `byter<value>` : Converts a list of numbers into a byte array.
- `chr<value>` : Converts a number into a character.
- `chrs<value>` : Converts a list of numbers into a string.

## String Modifiers

- `split<string, delimiter>` : Splits the string into a list every time the delimiter is found.
- `contains<string, value>` : Returns true if the string contains the value.
- `strUpper<string>` : Returns the string with all letters uppercase.
- `strLower<string>` : Returns the string with all letters lowercase.
- `strShift<string>` : Returns the string with all characters in the form they would be if you were to hold shift.
- `strUnshift<string>` : Returns the string with all characters in their form if you were to not hold shift. (Inverse of `strShift`)
- `substr<str, start, end>` : Returns the substring between the start and end indices.
- `replace<str, old, new>` : Replaces each instance of `old` in `str` with `new`.
- `escape<str>` : Escapes every escape sequence in the string. For example, `"\\n"` turns into `"\n"`.
- `unescape<str>` : Unescapes every escape sequence in the string. For example, `"\n"` turns into `"\\n"`.
- `parseNum<str>` : Parses the string as a number.

## Object Functions

- `getattr<instance, attribute>` : Uses the vanilla get method to access the instances value.
- `hasattr<instance, attribute>` : Returns true if the instance has the attribute in question.
