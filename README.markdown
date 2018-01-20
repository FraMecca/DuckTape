# DuckTape - Simple Reverse Proxy for local development

DuckTape is a simple reverse proxy server which will serve up a directory of files
and do simple proxying.  It is quite handy when developing Web
applications that do not depend on application servers and for local testing.

It is inspired by [tape](https://github.com/metajack/tape).


## Installation and Dependencies

DuckTape is built on top of Python and Twisted.

	pip install --user twisted

To install DuckTape, place the `ducktape` executable somewhere in your path.


### Usage

Every time DuckTape receives a connection, it check if the file exists in the folder it is serving;
if the file exists it is served directly, if it does not DuckTape acts as a reverse proxy.

```
usage: tape [-h] [-H HOST] [-P PROXY_PORT] [-p PORT] [directory]

Simple reverse proxy for local development.

positional arguments:
  directory             working directory, default: '.'

optional arguments:
  -h, --help            show this help message and exit
  -H HOST, --host HOST  host of the proxy, default: localhost
  -P PROXY_PORT, --proxy-port PROXY_PORT
                        listening port of the proxy, default: 8000
  -p PORT, --port PORT  listening port, default: 8080
```

Example:

	ducktape -p 8080 -P 5000 /project/dir -h localhost
