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
