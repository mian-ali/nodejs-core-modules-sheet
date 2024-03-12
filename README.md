# NodeJs Core Modules
Node.js core modules are a set of modules that come bundled with the Node.js runtime environment. These modules provide essential functionality for building various types of applications, ranging from web servers to command-line utilities. Core modules are included in Node.js by default, so you don't need to install them separately using a package manager like npm.

<p> Some common examples of Node.js core modules include:</p>

## REPL [NodeJs DC](https://nodejs.org/docs/latest/api/repl.html)

 <p>The node:repl module provides a Read-Eval-Print-Loop (REPL) implementation that is available both as a standalone program or includible in other applications</p>
 
Below are some commands you can use in the REPL (Read-Eval-Print Loop):

- `.break`: Sometimes you get stuck, this gets you out.
- `.clear`: Alias for `.break`.
- `.editor`: Enter editor mode (Ctrl+D to finish, Ctrl+C to cancel).
- `.exit`: Exit the REPL.
- `.help`: Print this help message.
- `.load`: Load JavaScript from a file into the REPL session. Example: `.load ./file/to/load.js`.
- `.save`: Save all evaluated commands in this REPL session to a file. Example: `.save ./file/to/save.js`.

Remember:
- Press Ctrl+C to abort the current expression.
- Press Ctrl+D to exit the REPL.

## Warpper Module
Before a module's code is executed, Node.js will wrap it with a function wrapper that looks like the following:

```javascript
(function(exports, require, module, __filename, __dirname) {
  // Module code actually lives in here
});
```
By doing this, Node.js achieves a few things:

- It keeps top-level variables (defined with var, const, or let) scoped to the module rather than the global object.
- It helps to provide some global-looking variables that are actually specific to the module, such as:
- The `module` and `exports` objects that the implementor can use to export values from the module.
- The convenience variables `__filename` and `__dirname`, containing the module's absolute filename and directory path.

` Module Wrapper`

In Node.js, before a module's code is executed, it is wrapped with a function that provides several parameters:

- `exports`: A reference to the `module.exports` that is shorter to type.
- `require`: Used to import modules.
- `module`: A reference to the current module.
- `__dirname`: The directory name of the current module. This is the same as the `path.dirname()` of the filename.
  Example: `console.log(__dirname);`
- `__filename`: The file name of the current module. This is the current module file's absolute path with symlinks resolved.
  Example: `console.log(__filename);`

 ## Path Module [DOC](https://nodejs.org/docs/latest/api/path.html)

The `path` module provides utilities for working with file and directory paths. It can be accessed using:

```javascript
const path = require('path');
```
**basename()** - The basename() method returns the last portion of a path, similar to the Unix basename command. Trailing directory separators are ignored.

**Syntax:*` basename(path[, ext])`

**Example:* `basename('/test/something.html', '.html')`

**dirname()** - The dirname() method returns the directory name of a path, similar to the Unix dirname command. Trailing directory separators are ignored.

**Syntax:* `dirname(path)`

**Example:* `dirname('/test/something.html')`

**extname()** - The `extname()` method returns the extension of the path, from the last occurrence of the `. (period)` character to end of string in the last portion of the path. If there is no `.` in the last portion of the path, or if there are no `.` characters other than the first character of the basename of path, an empty string is returned.

**Syntax:* `extname(path)`

**Example:* `extname('index.html')`

**join()** – The `join()` method joins all given path segments together using the platform-specific separator as a delimiter, then normalizes the resulting path. Zero-length path segments are ignored. If the joined path string is a zero-length string then `'.'` will be returned, representing the current working directory.

**Syntax:* `join([paths])`

**Example* - `join('/search', 'label', 'course/python', 'oop', '..')`

**normalize()** - The `normalize()` method normalizes the given path, resolving '..' and '.' segments. If the path is a zero-length string, '.' is returned, representing the current working directory.

**Syntax:* `normalize(path)`

*Example:*
```javascript
normalize('C:\\temp\\\\foo\\bar\\..\\');
win32.normalize('C:////temp\\\\/\\\/\\\/foo/bar');
```

- ` Note: The win32 property provides access to Windows-specific implementations of the path methods.`

**parse()** - The parse() method returns an object whose properties represent significant elements of the path. Trailing directory separators are ignored.

**Syntax:* `parse(path)`

**Example*: `parse('C:\\path\\dir\\file.txt')`

**isAbsolute()** - The path.isAbsolute() method determines if path is an absolute path. If the given path is a zero- length string, false will be returned.

**Syntax*:- `isAbsolute(path)`

**Example*:-
`isAbsolute('//server'); // true
isAbsolute("\\\\server'); // true
isAbsolute('C:/foo/..'); // true
isAbsolute('C:\\foo\\..'); // true
isAbsolute('bar\\baz'); // false
isAbsolute('bar/baz'); // false
isAbsolute('.'); // false`

## OS Module
### Operating System Module

The `os` module provides operating system-related utility methods and properties.

```javascript
const os = require('os');

or using ES6 syntax:
import * as os from 'os';
```

**platform()** - Returns a string identifying the operating system platform. The value is set at compile time. Possible values are `aix`, `darwin`, `freebsd`, `linux`, `openbsd`, `sunos`, and `win32`.

**arch()** - Returns the operating system CPU architecture for which the Node.js binary was compiled. Possible values are `arm`, `arm64`, `ia32`, `mips`, `mipsel`, `ppc`, `ppc64`, `s390`, `s390x`, `x32`, and `x64`.

**cpus()** - Returns an array of objects containing information about each logical CPU core.

**hostname()** - Returns the host name of the operating system as a string.
**hostname()** - Returns the string path of the current user's home directory.

**networkInterfaces()** - Returns an object containing network interfaces that have been assigned a network
address.

**freemem()** - Returns the amount of free system memory in bytes as an integer.

**totalmem()** - Returns the total amount of system memory in bytes as an integer.

## URL Module

# URL Module

The `url` module provides utilities for URL resolution and parsing.

```javascript
const url = require('url');
or using ES6 syntax:

import url from 'url';
```

```javascript
Example usage:

const myURL = new URL('https://www.example.com:8080/p/a/t/h?query=string#hash');

```

**hash()** - Gets and sets the fragment portion of the URL.

**host()** - Gets and sets the host portion of the URL.

**hostname()** - Gets and sets the host name portion of the URL. The key difference between` url.host` and `url.hostnam`e is that `url.hostname` does not include the port.

**href()** - Gets and sets the serialized URL.

**PORT()** - Gets and sets the port portion of the URL.

**protocol()** - Gets and sets the protocol portion of the URL.

**search()** - Gets and sets the serialized query portion of the URL.

**toString()** - The toString() method on the URL object returns the serialized URL. The value returned is
equivalent to that of url.href and url.toJSON().

**toJSON()** -  The toJSON() method on the URL object returns the serialized URL. The value returned is
equivalent to that of url.href and url.toString().






