# nodebook [![Build Status](https://travis-ci.com/netgusto/nodebook.svg?branch=master)](https://travis-ci.com/netgusto/nodebook)

Nodebook - Minimalistic code REPL with web UI

## What is it?

Nodebook is an in-browser REPL supporting many programming languages. Code's on the left, Console's on the right. Click "Run" or press <kbd>Ctrl</kbd>+<kbd>Enter</kbd> or <kbd>Cmd</kbd>+<kbd>Enter</kbd> to run your code.
Code is automatically persisted on the file system.

![nodebook](https://user-images.githubusercontent.com/4974818/45320903-2cdec280-b544-11e8-9b2e-067b646de751.png)

A notebook is a folder containing an `{index|main}.{js,py,c,cpp,...}` file. The homepage lists all of the available notebooks.

![home](https://user-images.githubusercontent.com/4974818/45320797-ed17db00-b543-11e8-91ae-db813debab5b.png)

## Supported environments

* C11 `(.c)`
* C++14 `(.cpp)`
* Go `(.go)`
* Haskell `(.hs)`
* Java `(.java)`
* NodeJS `(.js)`
* Lua `(.lua)`
* PHP `(.php)`
* Python 3 `(.py)`
* R `(.r, .R)`
* Ruby `(.rb)`
* Rust `(.rs)`
* Swift `(.swift)`

If `--docker` is set on the command line, each of these environments will run inside a specific docker container.

Otherwise, the development environments on your local machine will be used.

## Installation

```bash
$ git clone https://github.com/netgusto/nodebook
$ cd nodebook
$ npm install --production
```

## Usage

### Create a Notebook

In the directory where you want your notebooks to be stored, simply create a folder containing a file named `{index|main}.{js,py,c,cpp,...}`.

The notebook's name will be the name of the folder. The notebook language is determined automatically.

### Run the REPL

```bash
# Default usage; local execution, bound to 127.0.0.1:8000
$ node . --notebooks path/to/notebooks
# open http://127.0.0.1:8000 in a browser
```

```bash
# Set bindaddress and port
$ node . --notebooks path/to/notebooks --bindaddress 0.0.0.0 --port 12000
```

```bash
# Execute code in disposable docker containers (node:alpine)
$ node . --notebooks path/to/notebooks --docker
```

#### Command line options

* **--notebooks**: path to notebook folders; required
* **--bindaddress**: IP address the http server should bind to; defaults to `127.0.0.1`
* **--port**: Port used by the application; defaults to `8000`
* **--docker**: Execute code in disposable docker containers instead of local system; defaults to `false`

## ⚠️ A bit of warning ⚠️

Do not run this on a port open to public traffic! Doing so would allow remote code execution on your machine.

By default, the server binds to `127.0.0.1`, which allows connection from the localhost only. You can override the bind address using `--bindaddress`, but do it only if you know what you're doing.

## Develop

To iterate on the code:

```bash
$ npm install
$ NOTEBOOKS=path/to/notebooks npm run dev
```

To build:

```bash
$ npm run build
```

To test:

```bash
$ npm test
```
