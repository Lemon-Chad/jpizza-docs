
# Official Fridge Libraries

## Utils

`import utils;`
`get utils`

### Array Object

`utils::Array(type#String);`

#### Methods

- `push<object>` - Adds the object to the array if the types match.
- `size` - Returns the size of the array.
- `drop<obj>` - Removes that object from the array.
- `pop<index>` - Removes the object at the specified index.
- `set<index, obj>` - Sets the index to the given object.
- `get<index>` - Gets the object at the specified index.

#### Overrides

- `bracket<index>` - Returns the object at the specified index.
- `string` - Returns the array as a string.
- `type` - Returns "Type_Array", where 'Type' is the provided type.

### Map Object

`utils::Map(keyType#String, valueType#String);`

#### Methods

- `add<k, v>` - Adds the given key and value pair to the map if the types match.
- `del<k>` - Removes the given key from the map.
- `find<k>` - Returns the value associated with the key.

#### Overrides

- `bracket<k>` - Returns the value associated with the key.
- `access<k>` - Returns the value associated with the key.
- `string` - Returns the map as a string.
- `type` - Returns "KeyType_ValueType_Map" where 'KeyType' and 'ValueType' are their provided types.

## Socks

`import socks;`
`get socks`

### SocketConnection Object

**Note**: *You will never construct this object yourself.*

- `send<msg>` - Sends the client the given message.
- `recv` - Recieves data from the client.
- `close` - Closes the connection.

### Socket Object

`Socket(port#num);`

- `listen` - Returns a SocketConnection Object once a client connects to the server.
- `close` - Closes the server and all its SocketConnections.

### SocketClient Object

`SocketClient(host#String, port#num);`

- `send<msg>` - Sends the server the given message.
- `recv` - Recieves data from the server.
- `close` - Closes the connection.
