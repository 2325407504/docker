# Docker 1.0 architecture

## Introduction


## Engine API

The engine API is the canonical way to interact with the Docker engine programatically. All interactions with the engine
happen through the engine API, directly or indirectly. This includes:

	* Command-line operation of the engine
	* Remote access to the engine via the http remote api
	* Introspection from inside a container

The engine API is designed to natively support a few important things:

	* Isolation and multi-tenancy
	* Easy crud operations on structured data
	* Unix-style process execution, including sending and receiving any number of binary streams in parallel
	* Easy watching of value changes


### Connecting to the engine

The first step to using the engine API is to find an endpoint to connect to. This will depend on the context
in which your program is being executed.

If your program is running *inside* a docker container with introspection privileges, it can get an endpoint
by opening the unix socket at `/.engine.sock` in the containers filesystem.
The endpoint will be scoped to that particular container, and your program will not have access to
anything outside that scope.

If your program is running in the host, *outside* a container, it can get an endpoint scoped to any container by
opening the `.engine.sock` unix socket in the filesystem of that container.

To get full access to all containers in the engine, simply get an endpoint on the `root container` of the engine.
See [filesystem layout] for details.



### The beam protocol


### Inspecting a container


### Running jobs


### Available jobs


### Navigating containers





## Docker on the host


### Cross-platform support



### Runtime dependencies


### Plugins



### Filesystem layout


## Execution environment

### Environment variables



## Packaging and distribution




## Container format

### Configuration


### History


