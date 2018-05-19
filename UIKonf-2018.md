# UIKonf 2018

[Website](http://www.uikonf.com)

13th - 16th May 2018. 

450 + attendees. 41 countries.

18 talks.

## Tired of the state of online conversations? 🙈🙉🙊 Let’s do something about it 💪

[Kamilah Taylor](https://twitter.com/kamilah)

- Increased polarisation and decreased empathy from around the time of online social media.
- Polarisation is good for online platforms.
- Swaay is a company to make interaction more thoughtful.
- We should try to have conversations without requiring agreement.
- When building software ask "How can this harm people?".
- Technology will not solve everything - we also need political and personally responsibility.
- We have a moral obligation to make a difference where we can.


## The Magic of UI Testing

[John Sundell](https://twitter.com/johnsundell)

- Usually developers start with unit tests.
- Unit tests don't test how real users use the app.
- These aren't enough as things can still go wrong - we need integration tests.
- There is a continuum of Unit Tests → Integration Tests → End to End Tests. 
    - The time and complexity increased as you move rightwards.
    - However the tests also become less artificial, and test more like how real users use the software.
- Rather than Test Driven Development think "Tactically Deployed Development". That is test what has the most value.
- For example onboarding flow is only shown once, and so it is easy to regress.
- UI test can give you an insurance policy for these situations.
- UI tests such as onboarding can be flaky as they will fail after the first run of the app.
- You can use command line arguments set in the unit tests that the `AppDelegate` can read to control the app. For example `-skipOnboarding` or `-loadMockData`. This are also for debugging.
- Tip - use accessibility IDs rather than checking content which is likely to change.
- Use `waitForExistence()` rather than `sleep()`
- Split up your test suits and run them nightly, hourly, on a per pull/merge request basis.
- Webviews and interaction with other apps is hard, so don't try to UI test these.
- Tip - send a tap to dismiss an alert view.

## 10 Things you Need to Know before Implementing Cryptography

[Anastasiia Voitova](https://twitter.com/vixentael)

- Themis is a crypto libray for iOS
- Research shows that 83% of issues are due to misuse of crypto libraries, and not because of bugs in the libraries themselves.
- Remember - your security is a as strong as it's weakest part.
- Hide sensitive data when during multi-tasking by showing a screenshot upon entering the background.
- You should do input validation on both the client and the server.
- Use TouchID, FaceID, 2FA for better authentication.
- Avoid storing sensitive data (not just passwords) as plain text.
- cfph/clousau does static analysis to check for security flaws.
- Do SSL pinning.
- Obfuscate your code - use PPiOS-Rename or Obfuscater-iOS - but remember other forms of security are better done first.
- Consider adding a honey pot - e.g. a fake encryption key in a favourable location, then track usage of that key to catch malicious agents.

## Advanced Debugging Techniques

[Carola Nitz](https://twitter.com/_caro_n)

- 50% of developers time is spent debugging. Costing ~ $3.12 billion!
- Add a breakpoint in your main method to `import UIKit` and `import Foundation` to automatically have them when using lldb.
- You can use lldb to change a variable at run time.
- FBChisel
- Use `assert` and `assertFailure` for code that should no execute, e.g. default enum cases.
- `precondition` and `fatalError` will crash in all builds, even releases.

## MVC is not your problem

(Joachim Kurz)[https://twitter.com/cocoafrog]

- Apple says you should "split things into at least MVC".
- Can have other kinds of controller, such as a "ModelController". A fetched results controller is like this.
- Design for replacement rather than reuse.
- Reuse is hard, and normally takes around 5-9 times longer.
- Reuse often doesn't happen, only ~20% of the time.
- Designing for reuse is bad for an API. Instead reuse emerges rather than it being planned.
- Unlikely you will ever want to swap out implementation layers, .e.g. Core Data for Realm, so why build for it?
- Architecture planning often concentrates too much on the technical dimension. Could use the design dimension, i.e. how the UI is structured, to guide architecture instead.
- Architecture is hard to generalise. Aim to architect per use case.

## The Laws of Magic

[Dave DeLong](https://twitter.com/davedelong)

- If you took modern technology back in time it would be indistinguishable from "magic".
- We want satisfactory solutions. Three possible responses to a solution:
	- You mind is blown.
	- You say "well of course"
	- You have no reaction whatsoever.
- Example of a bad solution: the date and time API.
	- Ambiguous API, leads to incorrect usage of the API.
	- It is complex.
- Example of a good solution: the measurements API.
	- Can automatically convert measurements.
	- Define own types.
	- Is a focused API.
- Our goal is to minimise confusion and questions.
- Use conventions for familiarity
- Use inline documentation
- Use type safety to prevent illegal actions
- Use limitations to force you to be more creative and forces you into action.
- "Necessity if the mother of all invention"
- Limiting choices makes it easier 
- Expand what you have before adding something new.

## Scaling iOS, a story of technical debt, and how to get through it

[Vincent Garrigues](https://twitter.com/garriguv)

- Soundcloud for iOS originally built by contractors.
- Handover to in-house developers was short, ~2 months.
- Advice: rewrite will take longer than you think.
- They had to cut features to make the release date.
- They added no big features during the rewrite. As a consequence the Android app got further ahead.
- During a rewrite the team can get isolated and not know about what is coming.
- Each new feature increased the data model's complexity.
- Having everything connected in the data model means making changes difficult.
- Opening the data model made you cry 😭
- It took a longtime to migrate the database - had a negative impact on launch time.
- Had to consider how to handle the app being killed during DB migration. 
- Their architecture was very Core Data centric, and offline sync was coupled to search results.
- When the Xcode integration for Specta broke ~7k unit tests did not run!
- Today Soundcloud has 13k unit tests! (big round of applause from the audience 👏)
- Each feature gets it's own data store - not everything needs Core Data. 
- This is similar to microservice approach. Advice - talk to backend devs for ideas here.
- You should reevaluate technical strategy often.
- Use asserts to validate inputs. You may still ship a crash but you'll find it quickly.
- Confront your mistakes head on.
- Have a technical debt plan and get buyin from your team.
- Refactor progressively.
- Invest time in building tools that make your life easier.
