
# Native Libraries

## Time

`import time;`

- `halt<ms>` : Pauses the program for the specified amount of milliseconds.
- `stopwatch<func>` : Returns the amount of milliseconds taken to execute the specified function.
- `epoch` : Gets the current epoch time in milliseconds.

## Gens

`import gens;`

- `range<start, stop, step>` : Returns a list of numbers starting at `start` and ending at `stop`, increasing by `step`.
- `linear<start, stop, step, slope, y-inter>` : Returns a list of numbers starting at `start` and ending at `stop`, increasing by `step` with the function `x -> slope * x + y-inter` applied to each.
- `quadratic<start, stop, step, a, b, c>` : Returns a list of numbers starting at `start` and ending at `stop`, increasing by `step`, with the function `x -> a * x * x + b * x + c` applied to each.

## IOFile

`import iofile;`

### String Data

- `readFile<dir>` : Reads the contents of the specified file and returns the contents as a string.
- `writeFile<dir, string>` : Writes the string to the specified file. If the file does not exist, it will be created.
Returns true if the file had to be created, false otherwise.

### File Creation

- `fileExists<dir>` : Returns true if the specified file exists, else false.
- `makeDirs<dir>` : Makes all missing directories along the path.
- `deleteFile<path>` : Deletes the file at the given path.

### Directories

- `listDirContents<dir>` : Returns a list of the directories contents.
- `isDirectory<path>` : Returns true if the given path is a directory, else false.

### Working Directory

- `setCWD<dir>` : Sets the current working directory to the given directory.
- `getCWD` : Returns the path of the current working directory.

### Serialization

- `readSerial<dir>` : Reads and deserializes a stored JPizza object in the specified file and returns the object.
- `readBytes<dir>` : Reads the contents of the specified file and returns the contents as a byte array.
- `writeSerial<dir, value>` : Serializes the given value and stores it at the given path. If the value is a bytearray, the bytes will be written to the file. 
If the file does not exist, it will be created. Returns true if the file had to be created, false otherwise.

## Sys

`import sys;`

- `os` : Returns the users OS as a string.
- `home` : Returns the users home path.
- `execute<cmd>` : Executes the given command in the command line and returns the output.
- `executeFloor<cmdArgs>` : Executes the given command arguments in the command line and returns the output.
- `disableOut` : Disables output to the console.
- `enableOut` : Enables output to the console.
- `jpv` : Returns the current JPizza version.
- `envVarExists<var>` : Returns if an environment variable exists or not.
- `getEnvVar<var>` : Returns the value of the given environment variable. Throws an error if it doesn't exist.
- `setEnvVar<var, value>` : Sets the given environment variable to the given value.
- `getProp<prop>` : Gets the given system property.
- `setProp<prop, val>` : Sets the given system property to the given value.
- `exit<code>` : Exits the program with the given code.

## HTTPx

`import httpx;`

- `getRequest<url, headers>` : Sends a **GET** request to the given url with the given headers.
- `deleteRequest<url, headers>` : Sends a **DELETE** request to the given url with the given headers.
- `postRequest<url, headers, body>` : Sends a **POST** request to the given url with the given headers and body.
- `traceRequest<url, headers, body>` : Sends a **TRACE** request to the given url with the given headers and body.
- `patchRequest<url, headers, body>` : Sends a **PATCH** request to the given url with the given headers and body.
- `putRequest<url, headers, body>` : Sends a **PUT** request to the given url with the given headers and body.
- `optionsRequest<url, headers, body>` : Sends an **OPTIONS** request to the given url with the given headers and body.
- `connectRequest<url, headers, body>` : Sends a **CONNECT** request to the given url with the given headers and body.
- `headRequest<url, headers, body>` : Sends a **HEAD** request to the given url with the given headers and body.

## Pretzel

`import pretzel;`

- `init<host, port>` : Initializes the webserver on `host:port`.
- `route<addr, func>` : Whenever `addr` is queried, it sends data about the request to the function passed in, and sends back the data the function returns.
- `start` : Starts the webserver.

### Data

Route functions are given data that looks like this:
```json
{
    "method": "Request Method, usually GET or POST",
    "uri": "The uri used, like /test?abc=xyz",
    "body": "The body passed in.",
    "headers": {
        "the": ["headers given"],
        "from": ["post requests"]
    }
}
```

The expected return type should be of:
```json
{
    "code": 200, // The response code, like 200, 400, 404, etc.
    "header": "<h1>The value to return</h1>"
}
```


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
- `serverRecvBytes<connID, length>` : Recieves a byte array from the connection of the given length.
- `serverRecvAllBytes<connID>` : Recieves a byte array from the connection.
- `closeServerConnection<connID>` : Closes the given connection.

### Client Functions

- `clientSend<clientID, msg>` : Sends the server the given msg through the client.
- `clientSendBytes<clientID, bytearray>` : Sends the server the given byte array through the client.
- `clientRecv<clientID>` : Recieves data from the server.
- `clientRecvBytes<clientID, length>` : Recieves a byte array from the server of the given length.
- `clientRecvAllBytes<clientID>` : Recieves a byte array from the server.
- `clientClose<clientID>` : Closes the client connection.

## JSON

`import json;`

- `loads<string>` : Converts JSON string to a list/dictionary.
- `dumps<object>` : Converts a list/dictionary to a JSON string.

## AWT

`import awt;`

Colors for `awt` should be a list of 3 integers in the range 0 to 255, like `[255, 0, 0]` for red. `[r, g, b]`

To start using `awt`, you must call `awt::init()`. If not, all other functions will fail!

### Draw Functions

- `drawPoly<points, color>` : Draws a polygon with the vertices being the given points and shaded in the given color.
- `tracePoly<points, color>` : Draws the outline of a polygon with the vertices being the given points and shaded in the given color.
- `drawOval<x, y, width, height, color>` : Draws an oval of the given color with the center at (x, y) with dimensions width x height.
- `drawCircle<r, x, y, color>` : Draws a circle of the given color with the center at (x, y) and a radius of r.
- `drawRect<x, y, width, height, color>` : Draws a rectangle of the given color with the center at (x, y) with dimensions width x height.
- `drawRect<length, x, y, color>` : Draws a square of the given color with the center at (x, y) with dimensions length x length.
- `drawText<text, x, y, color>` : Writes text at (x, y) in the given color.
- `drawImage<x, y, filepath>` : Draws the image at the given path at (x, y).
- `setPixel<x, y, color>` : Sets the pixel at (x, y) to the given color.
- `drawLine<start, end, color>` : Draws a line from the start point to the end point in the given color.

### Config

- `setTitle<title>` : Sets the window title to the given title.
- `setSize<width, height>` : Sets the window dimensions to width x height.
- `setIcon<filepath>` : Sets the window icon to the given image.
- `setFont<name, type, size>` : Sets the current font to the given font with formatting of the given type and of the given size. Types include:
    - `"B"` -> Bold
    - `"I"` -> Italic
    - `"P"` -> Plain
- `setBackgroundColor<color>` : Sets the background to the given color.
- `lockSize<bool>` : Disables/enables the ability to resize the window.
- `setStrokeSize<width>` : Changes the stroke size.
- `exit` : Exits the window.

### Rendering

- `start` : Starts rendering and opens the window.
- `clear` : Clears the canvas.
- `refresh` : Refreshes the canvas.
- `refreshLoop` : Refreshs the canvas at 60fps in the background.
- `refreshUnloop` : Stops the refresh loop.
- `screenshot<filepath>` : Saves the current canvas to an image file which will be stored at the given path.
- `fps` : Returns the given FPS.
- `gpuCompute<bool>` : Sets gpu computing to true/false.

### QRendering

QRendering is an alternative to rendering. With the default rendering, any functions that modify the canvas, like drawing a circle, directly modify the canvas as soon
as they're called. With QRendering, the functions are put on to a sort of stack, and when you call the update command they are all drawn at once. This can help when
you're doing lots of drawing, as you might rerender the screen while only half of your drawing is complete. QRendering makes it so that everything will render at once.

- `toggleQRender` : Toggles QRendering.
- `qUpdate` : Pushs all the changes to the canvas.

### Mouse Input

- `mouseDown<button>` : Returns if the given button is being held down. `0` is LMB, `1` is MMB, `2` is RMB.
- `mousePos` : Returns the given mouse position as `[x, y]`.
- `mouseIn` : Returns if the mouse is in the window.

### Keyboard Input

Keys should be given as strings, like `"a"`, `" "`, or `"enter"`.

- `keyDown<key>` : Returns if the given key is being held down.
- `keyTyped<key>` : Returns if the key was pressed.
- `keyString` : Returns a string of all the pressed keys, like `"abc"` if keys A, B, and C were pressed.

### Audio

- `playSound<filepath>` : Plays the sound at the path.

### General Functions

- `chooseFile<path, filter, mode>` : Opens a file picker and returns the chosen file. Originates at the given path. Opens a save prompt if the mode is `awt::SAVE`, opens an open prompt if the mode is `awt::OPEN`. If the given filter is `null`, no filter will be applied. Otherwise, a filter should be given in the format `["Message to display", "extension"]`, such as `["PNG files (*.png)", "png"]`.

### Boilerplate

Some simple boilerplate code for creating an app is provided below.

```jpizza
import awt;
awt::init();

awt::setSize(800, 800);
awt::start();

awt::refreshLoop();
awt::toggleQRender();

awt::drawCircle(100, 400, 400, [50, 50, 50]);
awt::qUpdate();
```
