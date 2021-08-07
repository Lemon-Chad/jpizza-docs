# Bin Methods

## Type Methods

- `number` : Returns the object as a number.
- `boolean` : Returns the object as boolean.
- `dictionary` : Returns the object as a dictionary.
- `function` : Returns the object as a function.
- `list` : Returns the object as a list.
- `string` : Returns the object as a string.
- `type` : Returns the object's type as a string.

## Numerical Operations 

- `add<other>` : Returns the sum of the object and other.
- `sub<other>` : Returns the difference of the object and other.
- `mul<other>` : Returns the product of the object and other.
- `div<other>` : Returns the quotient of the object and other.
- `fastpow<other>` : Returns the object raised to the power of other.
- `mod<other>` : Returns the object modulo other.

## List Operations

- `append<other>` : Appends other to the object.
- `extend<other>` : Extends the object by other.
- `pop<other>` : Pops other from the object.
- `remove<other>` : Removes other from the object.
- `get<other>` : Returns `object.other`. (*Also used in dictionaries.*)
- `bracket<other>` : Returns `object[other]`. (*Also used in dictionaries.*)

## Conditionals

- `also<other>` : Returns true if either other, and the object are true, else false.
- `including<other>` : Returns true if both other, and the object are true, else false. 
- `eq<other>` : Returns true if the object equals other.
- `ne<other>` : Returns true if the object doesn't equal other.
- `lt<other>` : Returns true if the object is less than other.
- `lte<other>` : Returns true if the object is less than or equal to other.

## Object Operations

- `access<attribute>` : Returns the queried attribute.
