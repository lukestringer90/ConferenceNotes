# iOSCon 2017
[iOSCon2017](https://skillsmatter.com/conferences/8180-ioscon-2017-the-conference-for-ios-and-swift-developers#skillscasts)  was held at [CodeNode](https://skillsmatter.com/locations/264-skills-matter-codenode) on 30 and 31st March 2017.

Below are the notes I took. These should not be considered definitive or 100% accurate to the content presented - they are more a reminder of things I found interesting and useful. Where possible I have tried to find links to the slides or presentation material.

**Pull requests to correct inaccuracies are very welcome.**

---

## Balance 
[Saul Mora](https://twitter.com/casademora) - [SkillsCast](https://skillsmatter.com/skillscasts/9448-keynote-balance)- [Slides](https://speakerdeck.com/casademora/balance)

* Swift only a couple of years old
* Still learning to embrace swift and how it makes sense
* Main Swift tools we have are Functions, Protocols, Objects
* Swift blends a lot of approaches - Object OP, Functional OP, Protocol OP
* Throughtbot JSON parsing library - [Argo](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwi0rdXFuJzTAhVlDMAKHQwoBK8QFgglMAA&url=https%3A%2F%2Fgithub.com%2Fthoughtbot%2FArgo&usg=AFQjCNFuvn0HP_ybcBnRlMygI4xW3X7x-w&sig2=px1Mk90zZzpsGBmf7TuJrQ) .
* [Runes](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwiIr8DLuJzTAhWEBsAKHYIkCtEQFgglMAA&url=https%3A%2F%2Fgithub.com%2Fthoughtbot%2FRunes&usg=AFQjCNFMQCwcXb9A24YkEMNliBMLkSwmkQ&sig2=HbJoJz7y4h-0OV_5dB4CEA) library for operators
* Recommendation: use standard operators and less frameworks where possible
* Makes you code simpler, less complex and more familiar
* Use `map` and `flatMap` when using a `Result` type
* Use Promises to solve asynchronous throwing
* Obj-C is message based
* In Swift use `forwardingTarget(for:selector)` rather than `NSInvocation`
* Use a message / coordinator bus to allow a frameworks to communicate via Obj-C style messages
* A coordinator objects needs to define what the next coordinator is
* Swift compiler will complain when connecting, so use `AnyObject` to allow any message to be sent.
* In Swift, singletons are easier to write and therefore easier to abuse
* Use protocols to define a singleton. Then a concrete implementation can replace the default (static) singleton value.
* KVO in Swift is horrible!
* Compose an object by wrapping another. Take the wrapped object in the `init`
* Swift brings together lots of paradigms
* A general rule - use
	* Functions to calcualte state
	* Objects to present state (the UI)
	* Protocols for communicating state

## The Grant Tour of iOS Architectures
[Dan Cutting](https://twitter.com/dcutting) - [SkillsCast](https://skillsmatter.com/skillscasts/9578-the-grand-tour-of-ios-architectures) - [Slides](https://speakerdeck.com/dcutting/the-grand-tour-of-ios-architectures) - [Blog Post](http://cutting.io/posts/the-grand-tour-of-ios-architectures/) - [Example Code](https://github.com/dcutting/GrandTour) 

* Define “Architecture” as the internal structure within an iOS app
* Can be a divisive subject
* In “Apple MVC”, the view controller is often the root of the app
* View controllers do a lot!
* Long files are hard to understanding, testing is hard and muddles up model-view-controller
* Model-View-Presenter (MVP)
* Presenter talks to the view controller via a protocol. This makes is eraser to test.
* Model-View-View-Model (MVVM)
* MVP and MVVM are similar. In MVVM there is something like binding with the View-Model and the View-Controller. See RxSwift
* Usually all routing is done through the view controller (i.e. prepare for segue). Here the view controller needs to know about all the dependencies and the view controller is hard to reuse in a different context.
* Can use a Coordinator to combine all presenter objects. View controllers do not know about each other.
* Can use a hierarchy of coordinators.
* View-Interactor-Presenter-Entity-Routing (VIPER)
* In VIPER there are is a tonne of separation
* Based on the “clean architecture“ concept. Here UI is considered an external system.
* Inner rings cannot know about the outer rings.
* Uses the “need to know” principle
* Wireframe classes are responsible for routing. They inject dependencies.
* “Clean architecture” is not complete. VIPER and VIP are 2 implementations.
* Uber have their own implementation where routing is decoupled from the UI interactions.
* Testability is important in architecture.
* There should be a place for everything.
* Can lead to philosophical disagreements, so you need a solid team.
* Architectures can leads to lots of boilerplate code.
* Lots more types and lines of code for VIP, but each type is much smaller.
* Piecemeal refactoring is OK! Start with a single view controller.
* Stop extracting when happy with test coverage. Decide where on the spectrum is right - no separation vs complete separation.
* This spectrum (roughly) maps to difference between a design pattern and an architect.
* The more you take out of a view controller the easier it is to test.
* Core Data tentacles stretch thoughtout an app and it’s architecture (i.e. fetched results controller), therefore it is hard to treat it as an external system in the “clean architecture” sense.

# Architecting Alive Apps
[Jorge Ortiz Fuentes](https://twitter.com/jdortiz) - [SkillsCast](https://skillsmatter.com/skillscasts/9549-architecting-alive-apps) - [Slides](https://www.slideshare.net/jorgedortiz/architecting-alive-apps)	

* Architecture is beneficial when an application starts to grown
* Interactors encapsulate the use cases.
* Presenters decide what to do when the view is loaded. They setup and  then update a view.
* Entity Gateway is an interface to the persistence layer
* Inversion of dependencies uses an abstraction layer to decouple from a  framework
* Any abstraction is better than none
* For a good abstraction:
	* No reference to the framework. e.g. a Core Data wrapper cannot leak references to managed objects
	* Use your own data types. e.g. your own struct over an `NSManagedObject`
	* Use your own communication
	* Move implementation details into the abstraction type
* For a complex long term project, abstractions are very helpful. Decide them as you go.

## Generics and extensions in Swift
[Paweł Brągoszewski](https://twitter.com/epablito) - [SkillsCast](https://skillsmatter.com/skillscasts/9556-generics-and-extensions-in-swift)

* Can be more specific with a generic type by constraining it to a protocol
* Cannot nest a generic type inside a non-generic type. Must move it out of the non-generic type.
* Cannot have a generic function inside a generic type when the types do not match.
* Curiously Recurring Template Pattern - CRTP
* Swift 3 does not support circular generic type parameters (yet)

## Introduction to Functional Reactive Programming
[Eliasz Sawicki](https://twitter.com/EliSawic) - [SkillsCast](https://skillsmatter.com/skillscasts/9545-introduction-to-functional-reactive-programming) - [Slides](https://www.slideshare.net/EliaszSawicki/ioscon)

* Asynchronous data flows
* A stream of data over time. Previously used delegates, notifications etc
* Now we have `map`, `filter`, `reduce` to transform a stream
* rxmarbles.com
* ReactiveSwift was originally part of Reactive Cocoa
* A stream is called a “signal”
* A signal represents events over time
* A signal is observed
* A signal producer represents a task
* A “hot signal” always emits a value
* A “cold signal” only emits where this is an observer
* Bind signals to properties.
 
## The art of building UI reuse components
[Kevin Muessig](https://twitter.com/kevinmuessig)  - [SkillsCast](https://skillsmatter.com/skillscasts/9955-the-art-of-building-ui-reuse-components) - Slides

* Building reusable UI should adaptable, accessible, localisable and tintable
* Making a reuse component is like making an API
* Use interface builder for these benefits:
	* Less code
	* Better visibility
	* Easier debugging
	* Integrated tool support
	* Live preview
* `IBDesignable` to preview file in IB
* `IBInspectable` to expose `UIView` properties for IB
* `NibDesignable` does all the complicated stuff for you
* Use xib files for reusable views
* Use storyboard to reusable view controller and UI flows

## TDD in Xcode Playgrounds
[Paul Ardeleanu](https://twitter.com/pardel) - [SkillsCast](https://skillsmatter.com/skillscasts/10072-tdd-in-xcode-playgrounds) - [Slides](https://speakerdeck.com/pardel/tdd-in-xcode-playgrounds) - [Blog Post](https://m.pardel.net/tdd-ing-your-realm-objects-in-xcode-playgrounds-de492fa69543)

* Playgrounds offer fast feedback loop - a good fit for TDD
* Test or GTFO!
* Use `MyTestCase.defaultTestSuite().run()` in a playground

## Natural Swift
[Paul Hudson](https://twitter.com/twostraws)

Five Principles of Functional Programming
1. Functions are first-class data types
2. They can be used as parameters to other functions
3. Same inputs, same outputs; no side effects
4. Prefer immutable data types
5. Reduce how much state we track

* Benefits:
	* Trivial unit tests
	* Remove unexpected dependencies
	* Compose complex app from simpler, smaller parts
* Protocol Oriented Programming (POP) is similar to OOP but you use composition rather than inheritance 
* Can declare a protocol which simples combines other protocols to DRY up conformances

## Bringing Swift enums to Objective-C with macros
[Brandon Kase](https://twitter.com/bkase) - [SkillsCast](https://skillsmatter.com/skillscasts/9558-bringing-swift-enums-to-objective-c-with-macros) - [Slides](https://bkase.github.io/slides/adts-in-objective-c/#/) - [Sample Code](https://gist.github.com/bkase/3da9c46195961ed58bc8a7b1b05c1f87)

* It is possible to construct impossible object states in Obj-C, i.e. nil properties for a specific enum case
* Adding a new property can be forgotten when performing case analysis
* Swift enums help can help us, i.e. associated values
* `default` in switches breaks the safety of exhaustive analysis
* Macros are compiler directives to expand strings before compile time into Obj-C code
* `BKOneOf` macro used an Pinterest
* Macro cannot capitalise method names unfortunately 😞
* Errors are complicated when using the macro
* Xcode indexes and auto completion works!
* Swift enum also known as an Algebraic Data Type or Sum Type
* Use enum when you have mutually exclusive heterogeneous data
* “Rayified” turns something abstract into concrete

## It's about time
[Daniel Steinberg](https://twitter.com/dimsumthinking) - [SkillsCast](https://skillsmatter.com/skillscasts/9447-keynote-it-s-about-time)

* You day ends up filled with “stuff”
* But you lose this time time through the week
* It takes 23 minutes to return after just 1 minute of interruption , for both the interrupter and the interrupted.
* Working more hours becomes expected.
* The French have a healthy(er) work-life balance
* Only so much work you can do and maintain a suitable pace
* We make real connections outside of work (at the pub 🍻)
* Writers write first for a period, then edit later. This protects these blocks as they are different activities.
* Pomodoro - either focused or relaxes
* There are moments where you are not “there” as you are focused on something elsewhere.
* Focus on your purpose
* *What* is the most important?
* *Who* is the most important? (Don’t forget yourself)
* [Dutch Auction](https://en.wikipedia.org/wiki/Dutch_auction) is a metaphor to show you must schedule deliberately
* “The Future is here, it’s just not evenly distributed” - William Gibson
* It is valuable to say “I can’t do that”

## Composable Caching in Swift
[Brandon Kase](https://twitter.com/bkase) - [SkillsCast](https://skillsmatter.com/skillscasts/9559-composable-caching-in-swift) - [Slides](https://bkase.github.io/slides/composable-caching-swift/)

* Caches can be composed together
* Use “Futures” type to handle async callbacks
* Can model different layers in composition. Network → RAM → Disk
* An identity cache always misses
* An associative operator allows us to impose
* Now we have a monad!
* Transform caches so that types match between caches
* For example, a disk cache needs strings, network cache needs URLS
* This is a “virtual cache” as data is always transformed to get it
* Optimise by using in flight requests
* Stops unneeded network calls
* Can use the same in flight requests for different caches
* [Carlos](https://github.com/WeltN24/Carlos) library for this
* Can replace on disk cache with a full persistence framework, i.e. Core Data

## Dependency Injection in Practice
[Yoichi Tagaya](https://twitter.com/yoichitgy) - [SkillsCast](https://skillsmatter.com/skillscasts/9576-dependency-injection-in-practice) - [Slides](https://speakerdeck.com/yoichitgy/dependency-injection-in-practice-ioscon)

Sample Code: [Simple DI Container](https://gist.github.com/yoichitgy/30610aedd59babd70a848a9660164c75) , [Swinject Example](https://gist.github.com/yoichitgy/31762ed1bbe7dbbb7000decbfe0d64c2), [Cake Pattern](https://gist.github.com/yoichitgy/ed807c3fb674e49b4a0f7863d5d26b56) 

* Yoichi is the author on [Swinject](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwifh7O9r5zTAhWEC8AKHQGKAosQFgglMAA&url=https%3A%2F%2Fgithub.com%2FSwinject%2FSwinject&usg=AFQjCNEwmhWtVoGLExUgCjaW-8l9v8fgRg&sig2=Dq4XR-kYg7HbdlozDz4LDA)
* Inversion of Control allows to reuse dependencies
* Initialiser injection, property injection, method injection
* If implementation is tightly coupled to a concrete system then it is hard to test
* Loose coupling uses an abstract interface between them
* Dependency injection (DI) is managed by a container. This resolves dependencies.
* Register the dependency in the DI container
* Use `reflecting` on a string to get a unique hasahble key for any type `T`
* Can resolve to just a type, or the same instance of a type
* Dependency definitions are in a single place
* Cake Pattern: statically defined DI
* Protocol defines placeholder for dependency - the abstraction
* Another protocol defines the concrete dependency. This inherits from the abstract protocol, and an extensions makes in concrete
* Great article: [Dependency Injection with the Cake Pattern in Swift](http://acqui-hire.me/dependency-injection-with-the-cake-pattern-in-swift) by Bob Cottrell

## Do-It-Yourself Functional Reactive Programming
[Manuel M T Chakravarty](https://twitter.com/TacticalGrace) - [SkillsCast](https://skillsmatter.com/skillscasts/9610-keynote-do-it-yourself-functional-reactive-programming) - [Slides](https://speakerdeck.com/mchakravarty/do-it-yourself-functional-reactive-programming)

* React to change in structured safe manner
* Only mutate local properties
* Explicit streams of change propagation
* Track kinds of changes with types 
* A stream is a function mapping from time to values
* An associated type depends of the type of the protocol
