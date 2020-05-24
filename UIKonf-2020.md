# UIKonf 2020
May 18th-19th 2020, 

Held remotely using Hopin. A mixture of Youtube live streaming, screen sharing, Zoom and in-browser video calling.

## Who can say they have learned Swift?
**Paul & Sophie Hudson**

*  “Who can say they have learned Swift?” No-one can, there is too much to keep up with!
* Swift can evaluate new language features implemented first in other languages.
	* Swift can therefore benefit from their hindsight.
* Community should be more welcoming to other languages developers and newbies.
* We should add citations to talks, blogs etc as otherwise it looks like we people *just know* and this can be discouraging to newbies.

## Building a mobile-based startup business
**Dal Rupnik**

[Building a mobile-first startup business - Speaker Deck](https://speakerdeck.com/legoless/building-a-mobile-first-startup-business)

* Dal created a company to help children with speech problems.
* Founded company with other people who also had speech problems as children.
* Each person in the company had technical knowledge, but no knowledge of speech therapy or starting a business.
* You should validate an idea as quickly and as cheaply as possible.
* Startups often go through several MVPs and rewrites.
* You should look at similar apps to choose the right business model.
* Look for financial help from angel investors, private seed camps, accelerators and government funding.
* Remember that is unlikely you have a truly uniquer app.
* You could ask an influencer for help in promoting your app.
* You shouldn’t spend too much time on unit testing your MVP.
* Choose the right backend for your MVP. Consider:
	* What do you need as a minimum?
	* What can you afford?
	* What do you have preexisting technical knowledge of?

## Prepping For a SwiftUI Future
**Veronica Ray**

[Prepping For A SwiftUI Future - Speaker Deck](https://speakerdeck.com/mathonsunday/prepping-for-a-swiftui-future)

* Adopting MVVM (or similar) helps moving to SwiftUI.
* Swift UI only work on iOS 13 and above.
* For best results use SwiftUI and Combine together.
* Coordinator pattern ay not be suitable for SwiftUI. See this blog post: [Clean Architecture for SwiftUI - Alexey Naumov](https://nalexn.github.io/clean-architecture-swiftui/)

## The Multi-Threaded Asynchronous Parallel World of Swift
**Leo Dion**

[GitHub - leogdion/AsyncWorld](https://github.com/leogdion/AsyncWorld)

* Concurrent programming intersperses tasks.
* Parallel programming dedicated tasks to a core.
* Both approach can be combined.
* A process is 1 app running in the the OS.
* Each process can be split into threads, for example
	* Networking
	* UI
	* Background processing
* Asynchronous (NS)operations are hard and feel tacky.
* It is hard to repack errors and results.
* C# and JS use Promises and Futures. Offer some advantages:
	* No “callback hell” or “pyramid of doom”.
	* Can use functional functions for converting outputs.
* Swift Nio V2 has Promises and is used in server side Swift such as Vapor. Not suitable for iOS or macOS.

## Rich Text, Core Text
**Rob Napier**

* Swift has great handling of unicode and therefore emojis.
* A “code point” maps a number to abstract characters.
* This is a fundamental unit of language, independent of how it is drawn
* Emoji come from Japan, from a time where there were no colours on phone screens.
* A variation selector is used to modify an emoji.
	* Selector 15 is text version. This baselines the emoji like regular text.
	* Selector 16 is emoji version. This makes the emoji “hang” in the square.
* [Emojipedia](https://emojipedia.org/) documents all the emojis available.
* Some characters might have 2 unicode records. For example é:
	* Could be the combination of e and an accent
	* Or é in its own right
* Is possible to apply accents to emoji, but it looks weird.
* Zalgo is a method for combing random unicode together in the range `0x0300…0x036f`
* Combine a number with keycap to add a box around a number.
* Create flags using region letter. For example: region-u + region-s = 🇺🇸
	*  ISO committee wants to stay out of politics regarding what is and what is not a recognised country.
* Create regional flags (only works for GB currently). Combine:
	* Black flag: 🏴
	* Then region: `gb`
	* Then sub region: `sct`
	* Then cancel
	* = 🏴󠁧󠁢󠁳󠁣󠁴󠁿
* Emoji people accept a skin tone and gender modifier.
* Skin tone modifiers attach to any character, but only emojis actually combine them. Others keep them separate characters.
* There is a total of 25 combinations for the family emoji.
* Apple adds more details for their emoji glyphs at higher resolution. The largest keyboard on iOS ~47K glyphs!
* [GitHub - akfreas/emoji-extractor-plus: Extract emojis from Apple font in PNG format](https://github.com/akfreas/emoji-extractor-plus)

## Cross-platform Collaboration Patterns
**Miriam Busch**

[Cross-Platform Collaboration Patterns - Speaker Deck](https://speakerdeck.com/mbusch/cross-platform-collaboration-patterns)

* In a cross-functional team meeting only certain people are engaged as not all platforms are discussed at the same time
* 1 platform is often built after the other one, therefore playing the “catchup game”
	* The platform catching up has freedom in UI as one 1 platform has been delivered.
* From a technical point of view this is often harder and is better to consider everything up front at the same time.
* Naming is hard but is **super** important for everyone (code, documents, business etc) to agree on shared language.
* Unified UX ≠ unified UI.
* A design system can help in multi-platforms.
* Developers sometimes don’t like high fidelity designs as they know the canonical way to implement a feature better than designers.
* Managers should do code review!
* Cross platform pairing and code review for iOS and Android works.
* The API for iOS and Android is often shared..
	* Defining interfaces is quite waterfall but work.

## Building a Programming Language in Swift
**Chris Eidhof**

* Presentation done from a forest in 1 take!
* Building a language from scratch is a lot of hard work, but can be fun to learn!

## Swift Scripts: Zero to Hero
**Federico Zanetello**

[Swift Scripts: Zero to Hero 🦸🏼‍♀️ - Speaker Deck](https://speakerdeck.com/zntfdr/swift-scripts-zero-to-hero)
[talks/2020 Swift Scripts Zero to Hero at 52f0e697994c0528388b97da99f66f1440ef2e09 · zntfdr/talks · GitHub](https://github.com/zntfdr/talks/tree/52f0e697994c0528388b97da99f66f1440ef2e09/2020%20Swift%20Scripts%20Zero%20to%20Hero)

* Can create scripts in Swift as an alternative to using Ruby or Python.
* Create a Swift script through `spm` as an executable. Use the CLI rather than Xcode.
* `main.swift` is executed luke in a Swift playground.
* Can run from the terminal or open in Xcode.
* Get command line arguments using `CommandLine.Argumenents`
* Use `exit()` to terminate with `EXIT_FAILURE`
* Use `readLine()` synchronous function to get for user interaction.
* Environment variables from `ProcessInfo.environment`
* User `FileHandle` to get piped data.
* `ArgumentParser` library is from Swift Team. 
	* Add as a dependency.
	* Managers parsing arguments, flags etc for you.
	* Automatically prints errors if args are missing.
	* Prints out  `--help` text for free.
* Define a `ParsableCommand`
	* `@Argument` with name and help text.
	* `@Flag` also supported.
	* `run()` function that runs have all args are parsed.
* Tool Support Core - Basic and Utility - to add a progress bar, with updates, into the CLI.
* Using `build -c release` releases copies to the `local/bin`
* Use the runloop and `Dispatch.main` to do async work.

## Talk: Data Trusts: What, Why, How?
**Anouk Ruhaak**

[Open Letter - Anouk Ruhaak - Medium](https://medium.com/@anoukruhaak/open-letter-b7cb79832064)

 * Individuals acting independently for their own privacy also has collective consequences for everyone.
	 * Similar lesson during Covid19 pandemic.
 * Privacy: control over appropriate flow of information into given context. You may not want this shared in another context.
 * “Decision fatigue”:
	 * Who has time to think about sharing data (i.e. cookies) with each specific site?
	 * You just say “Yes” which is a flaw.
	 * Also begs the question: what is the point of a “Yes” if I can’t answer “No”?
 * Individual vs collective interest often decided on by the government.
 * A Data Trust is a legal instrument. It has fiduciary functions:
	 * Duty of loyalty - to the data subjects.
	 * Duty of care - not to be neglected.
 * Data Trustees make decisions that should be “good”.  Example:
	 * Data Subjects may be people with a disease who share their health data with a data trust.
	 * The Data Trustees must seek to further the goal of curing the disease, not to make money.
 * Data Subjects have collective bargaining power much like a union.
 * How do trustees get chosen? Elected?
 * How do they decide things? Voting?
 * Data Trusts seek consent, like in hospitals.
	 * Patients do not sign off every eventuality before surgery.
	 * Instead patients sign off high level risks, then they trust the surgeons to make the right decisions.
	 * Surgeons are still accountable.
 * Developers are often the first line of defence to make sound privacy calls.
	 * Customers and governments may not make sound decisions.
	 * Developers should ask these questions.
 * Example - contact tracing for Covd19.
	 * Bad time fo governments to be experimenting with big data
	 * Government could abuse this opportunity as there will be less scrutiny.
	 * Apple + Google protocol is de-centralised and is probably better.
	 * Contact tracing might not be the thing we should be contracting our attention on right now. Would be better to get testing infrastructure and solve other more pressing risks
 * Facebook have an “overview board” which is similar to a Data Trust. 
	 * This does not have a duty to the shareholder.

## We need to talk about Websockets
**Kristaps Grinbergs**

* Websockets = TCP IP Sockets + HTTP Requests
* Fully supported by Apple in iOS 13+
* 1 sides talks while the other side listens.
	* Two way
	* Single connection
	* Persistent
	* Low latency
* Can be used for real time data transfer.
* Connection handshake uses a GET request.
* The [Starscream Swift library](https://github.com/daltoniam/Starscream) conform to the websocket protocol.
* Can be tricky to debug.
* Useful tools for debugging:
	* Charles fo rmacOS.
	* Proxyman for macOS
	* Cleora for iOS supports web sockets + HTTP debugging 
* Long polling can be more stable and reliable than websockets.
* Radio will always be on so it could be bad for battery life .

## State Driven Development - The Beauty of Enums in Swift
**Conrad Stoll**

[State Driven Development - The Beauty of Enums in Swift - Speaker Deck](https://speakerdeck.com/cnstoll/state-driven-development-the-beauty-of-enums-in-swift)

* Bools are often used through a project to denote state.
* However it is not always clear
	* How bool values change,
	* What the dependencies in state changes are.
* Multiple bools for state adds complexity and it an opportunity for bugs to be introduced.
	* It is possible to have more permutations of bools than there are valid states.
	* “Tangled web of state”.
* Enums can be used instead.
* They help developers ask specific questions and prevent invalid states.
* Tempting to add a bool for something simple. Instead always use an enum as this is more extensible in the future.
* An enum can describe the lifecycle and the state of the program .
* An enum represent the single source of truth for view controller states.
* [GitHub - pointfreeco/swift-enum-properties: 🤝 Struct and enum data access in harmony.](https://github.com/pointfreeco/swift-enum-properties))
