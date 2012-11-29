#Learning from Open Source Software
##Changing paradigms in software development
###Abstract
####Software characeristics being subject of change
Software architecture - for example a switch from desktop to web-based applications or the replacement of tightly coupled interfaces with a distributed architecture.

This can often lead to technological changes like the use of a new programming language. Other technological changes could be related to support tools like source code management systems.

Testability is another important attribute of software. Large systems without an automated test-suite can 
easily be brought to a halt due to the unmanagable complexity.

Testability is part of the technical debt that can be attributed to a software project. Technical debt can also arise due to the lack of documentation or bad design choices.

####Lean Startup principles
Eric Ries embraces with his "Lean Startup" approach the principles of validated learning. Validated learning occurs when following a build-measure-learn cycle following clearly defined and testable hyptotheses.

This can be applied to initiate change in already existing software projects as well:  
We start by deriving scope for change from our business goals. The changes with the highest potential business value are selected and transformed into testable hypotheses.
In a pilot project we can then validate our hypothesis and pursue the change if its valid.
It is crucial that we define clear test metrics before-hand to ensure we are really validating our hypothesis.

####Moving to a pull-system
An example for a successful change is the transition of the source code management process of the Linux kernel.  
For years it has been managed by pushing patches up the chain to Linus Torvalds. This resulted in queues piling up as they could not be merged fast enough.  
Linus Torvalds developed git, a distributed content tracker, to replace the patch system.
This allowed for the transition from a push based to a pull based development system. A pull based system is exactly what lean software development suggests.  
Today, git empowers millions of open source developers in the world to follow this approach.  
Github, as a platform based on git, led to an explosion of open source collaboration in the last few years.

###Presentations
* [Interim presentation at Heidelberg University, 2012-11-15](https://github.com/mirkok/oss-seminar/blob/master/interim-presentation%20changing%20paradigms.pdf)

###Resources
* [Relevant papers](https://github.com/mirkok/oss-seminar/tree/master/resources)
* [Linus Torvals on SCM](http://marc.info/?l=linux-kernel&m=111288700902396)
* [Lean Startup Principles](http://theleanstartup.com/principles)