# Elixir and Phoenix - Personal Notes

# Elixir


# Phoenix

## Default Folder Structure 

The default structure looks similar to this:
- _build -> directory created by mix. Holds all compilation artifacts. (similar to a "build" folder in C, C++ and so on)
- assets -> directory where front end code is saved (JS and CSS).
- config -> directory where all project configuration is located.
- deps -> directory of mix dependencies. 
- lib -> directory of application code. Normally divided into two parts. For instance, assume there is an app called "MyApp". The lib folder will have a lib/MyApp and a lib/MyApp_web. The first is where the model / business logic resides. The last is where the controllers and views reside.  
- priv -> Where all resources necessary for production are located, but not necessarily part of the source code. Think of assets such as images, db migration scripts and so on. 
- test -> Directory of lib tests. 

## Architectural Design and Patterns
MVC based (similar as Ruby on Rails, Django, etc etc), but organized in a pipeline. Every module, behaviour and business logic is abstracted into "plug" components.

The "lib/MyApp" directory hold the "M" part. "lib/MyApp_web" holds the "V" and "C" part. 

All HTTP/s requests go through the phoenix application endpoint. The pipeline (Request Life Cycle is the other, correct name) calls several "plugs" from the plug library (this is a specification and library of how phoenix builds websites). 

Each layer represents a different purpose:
- Endpoint -> common and paths that all requests go through. 
- Router -> dispatch verb/path to controllers. May also restrict / scope certain features/functionalities. 
- Controller -> Retrieve request information, communicate with business logic and prepare data for presentation layer. (handle actions)
- View -> Handles structured data from controller and converts to presentation to be shows to users.


## Plug Library

Plug is a specification for composable modules in between web applications, acting as an abstraction layer for different web servers connection adapters. Basically,
it is a way to unify the connections we operate on. 
They are divided into two types:
- function -> Need to receive %Plug.conn{} as first parameter, options as second parameter and return one %Plug.conn{} as well. To use them, pass them as an elixir atom. 
- modules 