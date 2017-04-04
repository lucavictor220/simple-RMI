# Simple RMI 

## Description

Simple RMI project as the one in this repository should have 3 main classes: 
- Client
- Server
- Interface(one method in this example)

## Project structure

```
src/ 
    ---> example
                --->hello
                        ---> Client
                        ---> Hello(interface)
                        ---> Server
bin/

```

### Run project

First of all, in order to run a java project you need to compile the code. The compiled 
classes should be placed in bin/ which will have the same structure as the source code itself. 

```
# Clone repository
git clone https://github.com/lucavictor220/simple-RMI.git
cd simple-RMI

# create a bin folder
mkdir bin

# compile the source code and place it in bin/ directory with the same structure
javac -d bin src/example/hello/Hello.java src/example/hello/Server.java src/example/hello/Client.java

# navigate to bin/ folder to run rmiregistry 
# IMPORTANT: rmiregistry MUST be run in the same directory where the classes have been placed.
cd bin

# run rmiregistry
rmiregistry &

# navigate to root directory
cd ..

# run the Server
java -classpath bin -Djava.rmi.server.codebase=file:bin/ example.hello.Server 

# open a new tab and run the client
java  -classpath bin example.hello.Client

```
On the screen should appear:
`response: Hello, world!`

### Useful links

- I followed official documentation of oracle [here](http://docs.oracle.com/javase/7/docs/technotes/guides/rmi/hello/hello-world.html). 
- Read this about [env variables in java](https://docs.oracle.com/javase/tutorial/essential/environment/paths.html) 

### What I've learned

- RMI registry must be run in the classes directory
- Make sure you are not running another java processes on the same port. Kill all to make sure everything work properly.
- Classpath is an important variable you should take care of. 
- Codebase should point to classes directory