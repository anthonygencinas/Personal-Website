
# Actor Model 

----

## What is the Actor Model?

The actor model is a design model where concurrent executions talk to each other through the use
of units known as Actors through messages. By design Actors are Asynchronous. 


The Actor Model is built into the programming language [Erlang](https://www.erlang.org/). 

### Benefits of the Actor Model

#### Failures  are isolated.

If there is a failure in one Actor, then the other Actors aren't 
going to be immediately impacted by the failure. They will need to handle the failure once they need to use
information from the actor either directly or transitively.

#### By Design the Actor Model is Asynchronous  

Each Actor is on its own thread, meaning there is asynchronous execution occurring during execution.


#### Applications leveraging the Actor Model scales well.

You can deploy your application multiple times over. Considering you make your application stateless, it is
easy to deploy multiple instances of an application across multiple geographies.

----

## Why I choose to Stay Away from the Actor Pattern

For a typical production application I try to stay away from the Actor Model, unless it is required by the
applications' framework (e.g. [Akka](https://akka.io/)). While the actor pattern may scale well with code,
it creates a number of draw backs described below.

### It is difficult to create a decoupled application

Each Actor is tightly-coupled to all Actors it must communicate with. As each actor is dependent on the message from
its dependent Actors. This can exploit the issue of 
`"your application is as slow as it's slowest component"`.

### Concurrency is only at the Actor Level.

Each Actor is its own thread. Unless there are other design patterns used inside the Actor model, by
default there is only one shared thread. This introduced some inherit complexity from parallelism. The
performance of the application is coupled with the hardware it is running on.

### There are more Popular Applications which Implement Reactive Systems without the Actor Model

The actor model has the advantage of creating a reactive system and implementing parallelization seamlessly
in the application. However, there are other frameworks and models that have been used in favor.
Below are some examples. 

Please note while these frameworks have only been limited to JVM frameworks, you will find a similar 
pattern in the .NET ecosystem.

[Vert.x](https://vertx.io/) 

One example of an application that is reactive by nature and does not use Actors by default. 
Vert.x has an extensive library and has low latency. There is wide-spread support for Vert.x
and has extensive documentation behind it. Instead of using the Actor model to be reactive, it uses an
event bus, another reactive model.

[Spring Reactive](https://spring.io/reactive) 

Leverages the widely popular Spring Eco-System to build a reactive application. For already existing Spring 
applications it's easy to migrate to Spring Reactive without an expensive and time-consuming migration.
Additionally, Spring has extensive community support and documentation.


[Ktor](https://ktor.io/)

Leverages the ideology of Kotlin. Its syntax to create a highly reactive application. Learning Ktor is
simple if you already know Kotlin. The best parts of Kotlin are integrated with Ktor. Ktor works with already
existing Java Code so this can limit the scope of major changes to your application.



