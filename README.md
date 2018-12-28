# Sumac Protocol Specification [Work In Progress]
*Sumac* is a language agnostic protocol that facilitates object based communication between any two computer programs.

## Implementations
* Ruby: [ruby-sumac](https://github.com/robfors/ruby-sumac)

## Why Sumac Was Made
Let's start by imagining we were tasked with developing a project where one application needed to communicate with another application. Think in very universal terms. These applications could be simply separated by process, or they could be on physically separated by two computers running on opposite sides of the planet. Further, we also may be restricted to certain communication mediums. If we were building a dynamic website in JavaScript that needed to query a web server running our favourite language, historically we would be restricted to sending HTTP requests, but now a days we could take advantage of WebSockets. Whereas, if we needed to send commands to an Arduino project we may need to communicate over a serial connection. For other projects we have more freedom and can open raw TCP sockets. In all of these examples we would typically need to assume a client server model, with one application listening for connections, and the other with trying to initiate them.

If we were to design any of these projects we would typically need to build a communication layer consisting of three general components: a representation of the data we want to send, in a format that can be sent over the medium available; a layer in our client to convert our data to the new formant and send over the medium; and a layer in our server to convert what is incoming from the medium, back into the original data being sent. Further, if our application needs duplex communication we will need to add additional functionality to each layer. As you can probably see, a significant drawback with this traditional approach is that designing our own communication layer is a time consuming process. We may also find ourselves redesigning one each time we start a new project that has different constraints, communicates over a different medium or simply requires a different programming language.

Let's consider what we would have ultimately built after all this effort. To start, let's concider the data being sent. In most cases we will probably be using a object oriented language for each end of the communication, or at the very least, the data being sent can, or already is represented as objects. Essentially all we are building is a layer that takes objects from one object oriented program, converts them to a new format, sends them over a medium, then converts them back into the exact same objects on a different object oriented program. On a high level this whole procedure sounds kind of redundant and repetitive, doesn't it? Wouldn't it make sense if we could simply rely on the same protocol to facilitate communication of our data for the majority of our projects? This was the problem *Sumac* was made to solve.

## Design Objectives
*Sumac* was designed with a few important criteria and constraints.
* language agnostic: It must be able to be implemented on many different languages, allowing them all to communicate effortlessly.
* secure: Any implementation must enforce proper security practices such that it will be safe to use as a public facing API.
* support common language features: It should support common features universally found across most languages.
* simplicity: It should be simple as possible so it can be implemented and run on many devices. For very low resource devices such as microcontrollers, it is acceptable to limit some the protocol's functionality so long as any request for unavailable features can be handled gracefully by the remote end point.

## Alternative Solutions
*Sumac* was obviously not the first project attempting to solve such problems, however, it's objectives do differ enough to justify a new protocol.
Here are some alternative projects and how they differ, (please correct me if I have something wrong or missed something, as I don't have much experience with most of them):
* *DRb* :
    * only implemented for *Ruby* and supports features only available to *Ruby*
    * restricted to TCP communication
    * no access restriction for untrusted endpoints, would not be possible to host a public api
* *CORBA* :
    * Both endpoints need to have a description of the objects and methods that can be called (the IDL). Whereas an application using *Sumac* can try to call any method on any remote object, resulting in an exception when unavailable. The application's developer can document it's api however they want.
    * client can only call objects on the server, whereas *Sumac* supports full duplex communication as endpoints do not exist as client and server
* *RMI* :
    * only implemented for *Java* and supports features only available to *Java*



**TO BE CONTINUED...**

