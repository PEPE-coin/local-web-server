[![view on npm](http://img.shields.io/npm/v/local-web-server.svg)](https://www.npmjs.org/package/local-web-server)
[![npm module downloads](http://img.shields.io/npm/dt/local-web-server.svg)](https://www.npmjs.org/package/local-web-server)
[![Build Status](https://travis-ci.org/75lb/local-web-server.svg?branch=master)](https://travis-ci.org/75lb/local-web-server)
[![Dependency Status](https://david-dm.org/75lb/local-web-server.svg)](https://david-dm.org/75lb/local-web-server)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://github.com/feross/standard)

# local-web-server
A simple web-server for productive front-end development.

**Requires node v4.0.0 or higher**.

## Synopsis

Serve a directory on the default port:
```sh
$ ws
serving at http://localhost:8000
```

Blacklist certain paths, for example config files:
```sh
$ ws --forbid .json .yml
serving at http://localhost:8000
```

Reduce bandwidth with gzip compression:
```sh
$ ws --compress
```

Specify a Single Page Application:
```sh
$ ws --spa index.html
```

## Install
Ensure [node.js](http://nodejs.org) is installed first. Linux/Mac users may need to run the following commands with `sudo`.

```sh
$ npm install -g local-web-server
```

## Distribute with your project
```sh
$ npm install local-web-server --save-dev
```

Then add an `start` script to your `package.json` (the standard npm approach):
```json
{
  "name": "my-web-app",
  "version": "1.0.0",
  "scripts": {
    "start": "ws"
  }
}
```
This simplifies a rather specific-looking instruction set like:

```sh
$ npm install
$ npm install -g local-web-server
$ ws
```

to the following, server implementation and launch details abstracted away:
```sh
$ npm install
$ npm start
```

## Storing default options
To store per-project options, saving you the hassle of inputting them everytime, store them in the `local-web-server` property of your project's `package.json`:
```json
{
  "name": "my-project",
  "version": "0.11.8",
  "local-web-server":{
    "port": 8100
  }
}
```

Or in a `.local-web-server.json` file stored in the directory you want to serve (typically the root folder of your site):
```json
{
  "port": 8100,
  "log-format": "tiny"
}
```

Or store global defaults in a `.local-web-server.json` file in your home directory.
```json
{
  "port": 3000,
  "refresh-rate": 1000
}
```

All stored defaults are overriden by options supplied at the command line.

To view your stored defaults, run:

```sh
$ ws --config
```

## mime-types
You can set additional mime-type/extension mappings, or override the defaults by setting a `mime` value in your local config. This value is passed directly to [mime.define()](https://github.com/broofa/node-mime#mimedefine). Example:

```json
{
    "mime": {
        "text/plain": [ "php", "pl" ]
    }
}
```

## Log Visualisation
Instructions for how to visualise log output using goaccess, logstalgia or gltail [here](https://github.com/75lb/local-web-server/wiki/Log-visualisation).

## API Reference

<a name="module_local-web-server"></a>
## local-web-server
<a name="exp_module_local-web-server--localWebServer"></a>
### localWebServer([options]) ⏏
Returns a Koa application

**Kind**: Exported function  

| Param | Type | Description |
| --- | --- | --- |
| [options] | <code>object</code> | options |
| [options.forbid] | <code>Array.&lt;regexp&gt;</code> | a list of forbidden routes. |

**Example**  
```js
const localWebServer = require('local-web-server')
```

* * *

&copy; 2015 Lloyd Brookes <75pound@gmail.com>
