
# Native Libraries

## Time

`import time;`

- `halt<ms>` : Pauses the program for the specified amount of milliseconds.
- `stopwatch<func>` : Returns the amount of milliseconds taken to execute the specified function.
- `epoch` : Gets the current epoch time in milliseconds.

## IOFile

`import iofile;`

### String Data

- `readFile<dir>` : Reads the contents of the specified file and returns the contents as a string.
- `writeFile<dir, string>` : Writes the string to the specified file. If the file does not exist, it will be created.
Returns true if the file had to be created, false otherwise.

### File Creation

- `fileExists<dir>` : Returns true if the specified file exists, else false.
- `makeDirs<dir>` : Makes all missing directories along the path.

### Working Directory

- `setCWD<dir>` : Sets the current working directory to the given directory.
- `getCWD` : Returns the path of the current working directory.

### Serialization

- `readSerial<dir>` : Reads and deserializes a stored JPizza object in the specified file and returns the object.
- `writeSerial<dir, value>` : Serializes the given value and stores it at the given path. If the file does not exist, 
it will be created. Returns true if the file had to be created, false otherwise.

## HTTPx

`import httpx;`

- `getRequest<url, headers>` : Sends a get request to the given url with the given headers.
- `postRequest<url, headers, body>` : Sends a post request to the given url with the given headers and body.

## Sockets

`import sockets;`

**NOTE**: *The native sockets library is not recommended, it is easier to use the socks external library instead.*

### Constructors

- `newServer<port>` : Returns a server ID that can be used in other functions.
- `newClient<host, port>` : Returns a client ID that can be used in other functions.

### Server Functions

- `connect<serverID>` : Waits for a connection and then returns a connection ID that can be used in other functions.
- `closeServer<serverID>` : Closes the server and all its connections.

### Connection Functions

- `serverSend<connID, msg>` : Sends the given msg to the connection.
- `serverSendBytes<connID, bytearray>` : Sends the given byte array to the connection.
- `serverRecv<connID>` : Recieves data from the connection.
- `serverRecvBytes<connID>` : Recieves a byte array from the connection.
- `closeServerConnection<connID>` : Closes the given connection.

### Client Functions

- `clientSend<clientID, msg>` : Sends the server the given msg through the client.
- `clientSendBytes<clientID, bytearray>` : Sends the server the given byte array through the client.
- `clientRecv<clientID>` : Recieves data from the server.
- `clientRecvBytes<clientID>` : Recieves a byte array from the server.
- `clientClose<clientID>` : Closes the client connection.

## JSON

`import json;`

- `loads<string>` : Converts JSON string to a list/dictionary.
- `dumps<object>` : Converts a list/dictionary to a JSON string.
