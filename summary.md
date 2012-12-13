#Learning from Open Source Software
##Changing paradigms: Software characteristics
###Background
Most software is subject to constant change, driven by existing bugs, new business requirements, new technologies or refactoring undertakings.  
Keeping track of these changes and coordinating them with other processes is a major challenge for organizations.  
What can we learn by looking at how open source projects tackle this problem?  

We have selected some concepts of focus. Some of them do not directly represent software characteristics but are powerful concepts to guide the change of these.  
When we talk about scenarios like "changing a desktop application to a web based app", we will not gain much insight from merely listing the required technological changes.  
We learn much more by looking at generic processes that ensure a smooth transition of software characteristics.

*Open standards*: How do open source projects leverage open standards?  
We look at how HTTP and REST make projects like Node.js or CouchDB so successful.  
HTML5 is a collection of fundamental web standards - we will see how d3.js embraces them.

*Pull systems*: Toyota was one of the first discovering the power of pull-based systems - Taiichi Ohno called it Kanban. At the core of it is the desire to eliminate synchronous communication and thereby reducing waste and friction.  
David Anderson introduced Kanban's concepts to the world of software. In this section we will look at how github enabled an explosion of open source software collaboration by embracing similar pull concepts.

*Validated learning*: In this section we look beyond traditional open source projects. We will see how technology startups maximize their chance of success by guiding their decisions based on a validated learning process.

###Leveraging Open Standards and Protocols
How do open standards help to change software?

####Switching technologies
Lets assume you have identified the need to switch technologies.  
If your software is a big monolithic codebase with no standardized interfaces in between, you are in big trouble.	
Have you instead designed a decoupled system communicating over open protocols, you are free to replace any component with a new implementation using any technology.  
So why does not everyone build distributed, decoupled systems?  
The answer is simple, its just very hard to do in most development environments.

Open source projects like Node.js have changed that. Instead of abstracting away the networking from the developer, Node.js directly exposes standards like HTTP in a simple to use way.  
A complex HTTP interface can be implemented in Node.js in significantly less code than in traditional development environments like Java.  
But this is not the main advantage - as Node.js really directly exposes the HTTP standard, your implementation is much more aligned to how HTTP is intended to be used.  
Today, many applications "abuse" HTTP by using it as a RPC protocol (SOAP for example).  
If you instead write your interface implementation using HTTP as intended, you end up with a much more portable solution that can easily be re-implemented in different languages.

Following the same concept of rather being a tool to handle open standards instead of an abstraction of it, Protovis was rewritten as d3.js.  
Protovis is a library to create interactive, data-driven documents. Protovis is a monolithic framework, featuring abstractions of SVG, HTML and CSS. This enabled the concise description of data-driven documents.  
Mike Bostock, the main author of Protovis, rewrote Protovis into d3.js, a simple tool that allows powerful manipulation of the web standards directly. He discovered that removing the proprietary abstraction did not lower the complexity of the code using the library.  
Using d3.js has the major advantage that the developer using it not merely learns the proprietary API of a library but rather learns how to use SVG, HTML or CSS directly.  
Knowing the standards themselves makes developers less dependent on tools and thereby the tools easy to replace.

####Interoperating with different technologies
There is no swiss-army knife in software. For a set of problems there is always a set of ideal tools to use.  
If you want to implement a simple web app, Ruby on Rails is superior to J2EE.  
If you have to interface with complex SOAP engines, Java is probably superior to Ruby...

So if you want to exploit the best technologies for every problem at hand you need cross-technology mechanisms to communicate.  
HTTP was presented in the previous section and is a great solution for  communication between high-level components.  
Smaller modules of an application often cannot be cleanly mapped to HTTP resources - they should rather implement message-based or RPC communication.

Again, an open source project claims to bring the solution - ZeroMQ (ZMQ) calls itself "the intelligent transport layer".  
It is basically a high-level messaging library that provides the same API to communicate over TCP, IPC (inter-process) or inproc (in-process).  
This means you can implement a distributed system without having to physically distribute it or incur any performance hits if you do not want to.  
You can start by just using ZMQ to call a module that runs in the same process. At a later stage you could then simply move that module to a separate process or even to a separate machine.  
ZMQ not only gives you the messaging primitives but also entire messaging patterns like Request-Response, Publish-Subscribe etc.

Using ZMQ the Mongrel webserver could transition to an application and programming language agnostic architecture.  
It now makes it simple to combine multiple technologies behind a single HTTP interface - something many enterprises try to achieve.

####Moving parts
Using an open communication standard still does not solve a major problem all distributed systems have: independently moving interfaces.  
If for every API change of a service you have to change the implementation of every client, your system is not very distributed at all.  
A distributed system should allow each component to move independently from the rest.  
In 2010 Roy Fielding described a solution to this problem called REST - Representational State Transfer.  
Leonard Richardson split REST into levels of maturity:  
*Level 0*: This is where most services are at - simply using HTTP as a transport protocol but actually relying on RPC-style interfaces like SOAP.  
*Level 1 - Resources*: Instead of doing remote-procedure invocations on a singular remote, we request representations of resources. This makes our system much more decoupled as it does not tie the client to a particular remote.  
*Level 2 - HTTP Verbs*: All requests use HTTP verbs like GET, PUT, DELETE or POST. This adds another level of decoupling as it eliminates all shared state thats expected between client and service.  
We still need a shared understanding of which interactions are provided for each resource.
*Level 3 - Hypermedia Controls*: This is where we really tackle the problem of moving interfaces. Clients are not supposed to have any preconceived knowledge of URLs and which actions they support. They only know a single URL - the one of the service endpoint.  
The resource at this URL allows them to start navigating the service simply by following links. Every possible action on a resource is transmitted with the resource as a link.  
So in each response the service tells the client what it can do next - thereby making the service self-documenting.

Ruby on Rails is the most successful implementation of REST's concept. All resources and their actions can be navigated through links. The web interface can therefore be largely decoupled from the server.

####Test driven development
How is test driven development related to open protocols?

Test driven development is much more about the design process of software than the actual testing.  
Using TDD forces you to think about the right interfaces for your system.

Here we come to open protocols - if tests are all about your code's interfaces, why should you not directly write tests for open interfaces?  
Good tests should be decoupled from the implementation - so they should hardly change when your implementation changes.  
How could you make tests more stable than by relying on cross-platform protocols like HTTP?  
Even if you decide to switch platforms you can re-use your tests without any changes to test your new implementation.

###Moving to a pull-system
An example for a successful change is the transition of the source code management process of the Linux kernel.  
For years it has been managed by pushing patches up the chain to Linus Torvalds. This resulted in queues piling up as they could not be merged fast enough.  
Linus Torvalds developed git, a distributed content tracker, to replace the patch system.
This allowed for the transition from a push based to a pull based development system. A pull based system is exactly what lean software development suggests.  
Today, git empowers millions of open source developers in the world to follow this approach.  
Github, as a platform based on git, led to an explosion of open source collaboration in the last few years.

###Validated learning
Eric Ries embraces with his "Lean Startup" approach the principles of validated learning. Validated learning occurs when following a build-measure-learn cycle following clearly defined and testable hyptotheses.

This can be applied to initiate change in already existing software projects as well:  
We start by deriving scope for change from our business goals. The changes with the highest potential business value are selected and transformed into testable hypotheses.
In a pilot project we can then validate our hypothesis and pursue the change if its valid.
It is crucial that we define clear test metrics before-hand to ensure we are really validating our hypothesis.
