
wscat3 [![Build Status](https://img.shields.io/travis/ArtiomL/wscat.svg)](https://travis-ci.org/ArtiomL/wscat)
======

Unix-style WebSocket cat (or netcat for websockets).


Installation
------------

```
npm install -g wscat3
```

Usage
-----

```
$ wscat -h
usage: wscat [-h] [-v] [-l PORT] [-b] [-k] [-d] [-s SUBP] [address]

Positional arguments:
  address

Optional arguments:
  -h, --help            Show this help message and exit.
  -v, --version         Show program's version number and exit.
  -l PORT, --listen PORT
                        Start a websocket server on PORT.
  -b, --binary          Use binary WebSockets.
  -k, --keep-open       Do not close the socket after EOF.
  -d, --deflate         Use per-message deflate.
  -s SUBP, --subprotocol SUBP
                        WebSocket subprotocol

```

Examples
--------

If you ever used `nc`, `wscat` works pretty much the same.

### Connect to a server

```
$ wscat echo.websocket.org
Hello
Hello
Who's there?
Who's there?
^D

```

### Chat

Server:

```
$ wscat -l 12345
Hi there!
Hi!
It's nice to speak to someone who just dosn't repeat everything I say back at me.
Yeah! Isn't it?!
Sorry, gotta run...
^D

```

Client:

```
$ wscat localhost:12345
Hi there!
Hi!
It's nice to speak to someone who just dosn't repeat everything I say back at me.
Yeah! Isn't it?!
Sorry, gotta run...
```

### Transfer a file

Server:

```
$ wscat -b -l 12345 < ~/Desktop/mycat.jpg
```

Client:

```
$ wscat -b localhost:12345 > igotacat.jpg
```

Note that you can have the client send the file as well, after the connection has been setup `wscat` does not differentiate between server/client.
