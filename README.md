# Node Console
```
                __
|\| _  _| _    /   _ __  _  _  |  _
| |(_)(_|(/_   \__(_)| |_> (_) | (/_

```

## About

This module extends Node.js basic repl functionality:

* Makes all js files global
* Makes all packages included in package.json global
* Awaits promises (not perfect yet).
* Writes commands to a local history file.
* Configurable behavior using env variables or a nc.js file.

## Usage

install it using `npm install -g node-nc`

Enter `nc` to use the console.

![nc](https://raw.githubusercontent.com/nikostoulas/node-nc/master/usage.gif)]

## Configuration

```javascript
const defaultConf = {
  useGlobal: false, // Repl useGlobal. If set to true all globals will be inside nc namespace.
  useAsync: true, // Experimental use of await in repl.
  globalizeFiles: true, // Make all project files global. 
  globalizeDependencies: true, // Globalize projects dependencies.
  useNcFile: true, // Use nc.js file if found
  usePackageFile: true, // Use package file to determine prompt, root folter and dependencies.
  writeHistoryFile: true, // Write all commands to a file.
  historyFileName: '.node_history' // The filename. An absolute path can be given.
};
```

Configuration can be overwitten

* by env variables:

  NC_USE_GLOBAL, NC_USE_ASYNC, NC_GLOBALIZE_FILES,
  NC_GLOBALIZE_DEPENDENCIES, NC_USE_NC_FILE, NC_USE_PACKAGE_FILE,
  NC_WRITE_HISTORY_FILE, NC_HISTORY_FILE_NAME or
* by using an nc.js file. This file can also be used to make some project initializations

  Eg. connect to a database, declare some global vars etc.
  In nc.js a method setConfig(options) is available to overwrite the default configurations.

  Note that NC_USE_NC_FILE env variable must not be false.

  Eg:

  ```javascript
    setEnv({useGlobal:true}); // it only overwrites useGlobal config.
  ```

