So, I just started a new job where they use a lot of java.
I just spent the whole day getting an extremely simple service to build on my computer, and I'm so incredibly frustrated with this process I could scream.
First, I don't really know java syntax, so I keep having to look it up.
But that's not really a problem.
Sure, I had nfc what `Collection<? MyWierdObjects> Bob` meant, but I quickly found out!

No, I expected to need to learn java syntax when I started this job.
The problem is that I don't just have to learn the syntax, I have to learn the entire ecosystem.
And not just a few tools; I already read a bunch of documentation on Ivy and Maven and Ant, for instance, but this is still relatively straightforward.

No, it gets much worse.
The code that I'm working with is using the twitter-commons library, and also Google's guice.
I literally can't do ANYTHING without understanding how these libraries function.
My application doesn't have a `main()` -- you start it by launching the twitter app launcher and feeding it your class and it does a bunch of background magic to actually start it.
I see web servers being created (not documented, mind you -- I have to read the code on the particular web server module in use) as a servlet, but then it's never started even though that's what the module says to do.
Apparently the `start()` method is being called magically elsewhere.

Oh, none of these modules are ever actually instantiated.
Every single goddamn object here is 'injected' by guice, which I don't even know what the hell that means.
I want to pass an argument to a module, but I cannot because it's never instantiated as far as I can tell.
Instead, I get an instance by calling the injector's `getInstance` function, so I have to understand how that works before I can make a simple parameter change.

Building this is a nightmare.
I spent 3 hours building a proper pom file for maven to contain exactly the right set of 500 million dependencies.
And then -- big surprise! -- some of those dependencies have changed, and so supposedly "working" code won't build against 'em anymore.
So now I'm trying to understand these undocumented libraries to figure out how to work around their changes, except I don't understand any of the code because it's a rat's nest of injectors and abstract classes and bullshit.

Oh, and this is all for a logging application I could write in maybe 300 lines of python...
Kill me now.
