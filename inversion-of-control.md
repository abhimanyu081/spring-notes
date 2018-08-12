# What is Inversion of control?

**Component**  
I use component to mean a glob of software that's intended to be used, without change,
by an application that is out of the control of the writers of the component. By 'without
change' I mean that the using application doesn't change the source code of the
components, although they may alter the component's behavior by extending it in ways
allowed by the component writers.  

**Service**  
A service is similar to a component in that it's used by foreign applications. The main
difference is that I expect a component to be used locally (think jar file, assembly, dll, or a
source import). A service will be used remotely through some remote interface, either
synchronous or asynchronous (eg web service, messaging system, RPC, or socket.)

**The question is: "what aspect of control are they inverting?**" When I first ran into
inversion of control, it was in the main control of a user interface. Early user interfaces
were controlled by the application program. You would have a sequence of commands
like "Enter name", "enter address"; your program would drive the prompts and pick up a
response to each one. With graphical (or even screen based) UIs the UI framework
would contain this main loop and your program instead provided event handlers for the
various fields on the screen. The main control of the program was inverted, moved away
from you to the framework.

For this new breed of containers the inversion is about how they lookup a plugin
implementation. In my naive example the lister looked up the finder implementation by
directly instantiating it. This stops the finder from being a plugin. The approach that these
containers use is to ensure that any user of a plugin follows some convention that allows
a separate assembler module to inject the implementation into the lister.
As a result I think we need a more specific name for this pattern. Inversion of Control is
too generic a term, and thus people find it confusing. As a result with a lot of discussion
with various IoC advocates we settled on the name Dependency Injection.

# Forms of DI


* Interface Injection
* Setter Injection
* Constructor Injection

**Why prefer Setter Injection?**

