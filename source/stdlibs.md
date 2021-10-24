# Standard Libraries

## STD

`import std;`

### Enumerators

#### Option

*Public*

Serves as a way to dynamically and safely return a nullable value.

Best served with pattern matching.

- `Some { val }`
- `None`

#### StaticOption

*Public*

Serves as a way to statically and safely return a nullable value.

Best served with pattern matching.

- `Box(T) { val: T }`
- `Empty(T)`

### Classes

#### Array Class

`Array(..items)<T>;`
The Array class serves as an object oriented statically typed list. You can, of course, use the **any** type to dynamically type it.

- `add<item #T>` - Adds the given item to the array.
- `remove<item #T>` - Removes the given item from the array.
- `insert<item #T, index #num>` - Inserts the given item at the given index.
- `iter<func #function>` - Returns an *Iter* class that uses the given function and iterates over each item in the array.
- `pop<index #num>` - Pops the given index from the array and returns the item.
- `size` - Returns the size of the array.
- `addAll<..items>` - Adds all the items to the array.
- `slice<start #num, end #num>` - Returns a slice of the array between indices `start` and `end`.
- `indexOf<item>` - Returns the index of the given item.
- `contains<item>` - Returns true if the array contains the given item, else false.
- `join<str #String>` - Returns a string where each item in the list is seperated by the given str.

#### Map Class

`Map(..pairs)<K, V>;`
The Map class serves as an object oriented statically typed dictionary. You can, of course, use the **any** type to dynamically type it.

When constructing the map, you should provide each key value as pair, such as `["a", "b"]` or `[1, 2]`.

- `get<other #K>` - Returns the value associated with the given key. Fails if the key is not in the map.
- `getOrDefault<other #K, default>` - Returns the value associated with the given key. If the key is not in the map, returns the provided default.
- `set<key #K, value #V>` - Sets the given key in the map to the given value.
- `del<key #K>` - Deletes the given key from the map.
- `iter<func #function>` - Returns an *Iter* class that uses the given function and iterates over each pair in the map.
- `size` - Retruns the size of the map.
- `contains<key>` - Returns true if the map contains the given key, else false.
- `keyArray` - Returns an array of each key in the map.
- `pairArray` - Returns an array of each key-value pair.

#### Iter Class

*Should not be constructed manually*
Allows you to iterate over values in unique fashions.

- `collect` - Returns each item iterated over as a new object.
- `stream` - Iterates over each item without returning any values.

#### Tuple Class

`Tuple(..items);`
Offers as a way to statically return several different types in an immutable fashion.

- `size` - Returns the size of the tuple.
- `contains<item>` - Returns true if the tuple contains the given item, else false.

## Socks

`import socks;`

### SocketConnection Object

**Note**: *You will never construct this object yourself.*

- `send<msg>` - Sends the client the given message.
- `sendBytes<bytearray>` - Sends the client the given byte array.
- `recv` - Recieves data from the client.
- `recvBytes<length>` - Recieves a byte array from the client of the given length.
- `recvAllBytes` - Recieves a byte array from the client.
- `close` - Closes the connection.

### Socket Object

`Socket(port#num);`

- `listen` - Returns a SocketConnection Object once a client connects to the server.
- `close` - Closes the server and all its SocketConnections.

### SocketClient Object

`SocketClient(host#String, port#num);`

- `send<msg>` - Sends the server the given message.
- `sendBytes<msg>` - Sends the server the given message.
- `recv` - Recieves data from the server.
- `recvBytes<length>` - Recieves data from the server of the given length.
- `recvAllBytes` - Recieves data from the server.
- `close` - Closes the connection.
