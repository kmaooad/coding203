# Client notifications 

**Goal:** design notifications engine in communication app (like Microsoft Teams).

**Format:** work in group of 2-3 people. (Note: "2-3" means exactly 2 or 3. Not 1, not 4.)

**Deliverables:** assignment acceptance criteria consist of 
1) correct (compilable!) code; 
2) passing unit tests with reasonable coverage (>80%); 
3) diagram of _explicit and implicit_ dependencies (simplified UML-style: only boxes and arrows).

[Join assignment in GitHub Classroom](https://classroom.github.com/)

---------

## I. Behavior

From _end-user point of view_, app should have capabilities listed below. **Note**: these are top-level requirements, internal design will be more sophisticated. **You have to decide on your own about all the details: proper entry points and their format, necessary storage etc.**

### What's special here

What makes this task special is that it's much more 'abstract' than previous two. There are no predefined 'features' given. Mainly because they are just not known at the moment. We only know that we need some cool and very flexible engine to handle current and future needs about broadcasting notification to all connected client apps (mobile, desktop, web). 

### What the idea is

The idea is that our communication app (say MS Teams) has certain events that must be immediately delivered to client apps. Precise list of events is not important now, because it may change very soon as app evolves and more features are added. Notifications engine is something that spans across many other features.

### What the events are

Events can be: new message, incoming call, message liked, user mentioned, message read, user is typing, user presence changed etc etc etc.... many more can be added and some may go.

### Some rules

Tricky part is that different events are delivered differently. Core principles are listed below: 
1. Some notifications should be delivered to all user devices, some only to the specified ones. E.g. expired login session notification is sent only to the device where it was initially used.
2. Users may choose in preferences to deliver notifications to mobile devices only if they are not active on desktop; otherwise notifications are delivered to all devices.
3. Some notifications (e.g. calls, new messages) require to be sent as mobile push notifications. Usually this is done through special service should be used (e.g. Google Firebase or similar). But other events are sent through simple WebSocket channel, like presence changes, typing indicator etc. Such events don't appear as mobile notifications and are applicable only when app is in use.

## II. Implementation

### Scope

No need to implement a fully-functional application. You have to design only a library with requested functionality (i.e. logic of sending client notifications). All 'external' parts like DB, WebSocket host, push notification service etc. are out of scope here. Just design the layer where interact with them in some way, no need to make real calls to any real DB etc. Design what inputs you expect, what output return, and what side-effects produce (calls outside).

### Tests

You have to cover your code with unit tests as much as possible (>80% coverage). Code included in this repository gives a sample of writing unit test for `download()` function from "Refunds" project from lectures. You can use given project structure for your implementation.

To run tests, in tests folder `KmaOoad.Coding.203.Tests` run command `dotnet test`.
 

### Development setup

* latest .NET 5 SDK ([link](https://dotnet.microsoft.com/download/dotnet/5.0))
* editor of your taste, e.g. Visual Studio OR Visual Studio Code with Ionide and Omnisharp extensions OR JetBrains Rider (see more here for [Linux](https://fsharp.org/use/linux/), [Windows](https://fsharp.org/use/windows/), and [Mac](https://fsharp.org/use/mac/))




