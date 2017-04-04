# Simple RMI 

## Description

Simple RMI project as the one in this directory should have 3 main classes: 
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
# run rmiregistry, for Solaris check this link
rmiregistry &
# navigate to root directory
cd ..
# run the Server
java -classpath bin -Djava.rmi.server.codebase=file:bin/ example.hello.Server &
# open a new tab and run the client
java  -classpath bin example.hello.Client

```
On the screen should appear:
`response: Hello, world!`