# Sumac
*Sumac* is a language agnostic protocol that facilitates object based communication between any two computer programs.

## Implementations
* Ruby: [ruby-sumac](https://github.com/robfors/ruby-sumac)

## Why Sumac Was Made
Imagine you are building a website that needs to comuncatie with your server to obtain some data. The current standard approach is to make HTTP requests from the client to the server. You woud deveop: a representation of your data in a format that can be sent over HTTP; a layer in your client to convert your data to HTTP requests; and a layer in your server to convert HTTP requests back into the orginiganl data to sent. If you also need duplex communication this will further complicate each layer. The main problem with this approach is that you will need to rebuild each compoinedt for each new application you develop. Woudnnt it make sense if you used a ready make framework to .......
