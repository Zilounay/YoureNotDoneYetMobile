# You're Not Done Yet - The Mobile Checklist

## Table of Contents

//This is more of a TODO list more than anything right now
1. Intro
2. Text Inputs
3. Other Inputs (checkbox, switches, mutually exclusive controls)
3. Error Management (exceptions, crashes, alerts, displaying errors)
4. Navigation (push, pop, tabs, modal, screen rotation)
8. Background (saved state, springboard card)
5. Connectivity (wifi, slow edge, 2G, 3G, 4G, intermittent, zero-bytes, offline, plane mode) and hardware connectivity (usb, nfc, bluetooth, wifi)
6. Localization (of text & images, in various settings on the phone language vs app language vs current region)
7. Interruptions (accepted calls, declined calls, sending/receiving SMS, power cycle, restart, sending/recieving notification, alerts, low memory, home screen, switching apps, plane mode, out of storage) : should mean the app can stop itself, pause itself, and recover at the correct screen and in the correct state whenever going into background or being interrupted by any mean. Answering apps *from the notification*.
9. Storage (is everything stored properly, without risks, at the right place)
10. Security (
      Is your application storing payment information or credit card details?
      Does your application use secure network protocols?
      Can they be switched to insecure ones?
      Does the application ask for more permissions than it needs?
      Does your application use certificates?
      Does your application use a Device ID as an identifier?
      Does your application require a user to be authenticated before they are allowed to access their data?
      Is there a maximum number of login attempts before they are locked out?
      Customers’ Payment data security
      Network protocols security for running applications
      Breach in applications’ security and error reporting
      Authenticating application certificates and permissions
      Automatic Application lock out upon continuously entering invalid
      )

11. Accessibility (software buttons, zooming, font sizes, text to speech, ...)
12. Performance (battery usage, CPU usage, memory usage (and leaks), storage (disk vs card) management, responsiveness, screen size, time to launch app, time on launch screen, heavy load screen / yous should spread loads, continuous key press ) Whatever happens should be dealt with smoothly with a nice prompt and clear reaction.
13. Background work (doing work outside of main thread to not block UI, but also not have massive work when app is "idle" or in background, draining battery/data/etc)
13. Integration (does the camera, GPS, bluetooth work fine with the app)
14. Backwards compatibility, hardware compatibility : check all versions of all devices if possible. App must be installable and fully usable (unless features are not available on that device)
15. Images : correct size & weight on all devices and orientations. Not stretched, not pixelated, not too HD, etc.
16. Social : security & privacy policies are available, user can log out or opt out. users are prompted of what can/will happen when they give rights AND when said thing (posts/shares/likes) happens.
17. Ads (displayed/hidden when they should, display appropriate content)
18. Timezones : remote calls/times vs phone time vs current region time => use UTC everywhere anyway, transform into local time in the view
19. Stores : App is visible only in the stores you want/need (iOS AppStore, PlayStore, Android Market, etc.), and is visible only on compatible devices. Tablet app should not be visible in smartphone store. Store page is up to date with version updates, description, name/number, testers notified before release,
20. Pre-release checks / pre store checks (so that store review should pass)
21. App icons are available in all required formats ; store icons are available ; all app images are available in all formats (1x, 2x, 3x, etc.)
20. OS compatibilities, crossplatform compatibilities (does it work on iOS / Android/ Windows Phone how it should?)
21. Version compatibilities : does it work in iOS 9, 10, 11, 12? Test your target AND all the versions you are supposed to support
22. Does it work on all devices on all versions ? : iPhone, iPad, iPhone X, iPhone #S, and also android (OMEGALUL)
23. Orientations (error messages, videos, splashscreen, navigation and regular screens in all orientations, on all device sizes)
24. Sound (stops when going to background? Keeps going? Displays a notification ? Is controllable in control center / remote player)
25. Notifications (are sent when they should, are rich? deep linked? Modify badge ? Badge updates itself when app is read? geofenced? platform specific / feature specific. More to look up @pushwoosh for examples)
27. Gestures

//Actual TODO list of stuff I don't want to forget
- Add links to table of contents when document is close to being complete (or at least not structurally change too much)
- 

## I : Intro
### a : What is this list
What is this about ? This is about testing your app thoroughly and completely. This list will include as many elements as possible that you should test. Many of which you probably have already tested, some that you might have not thought about. This is about checking all the boxes and either validate the fact that you did indeed test X & Y, but that you also decided to ignore Z. Many of the elements of the checklist might not apply to you, because your app does not have that specific feature or does not use a specific technology. You might also simply want to skip some of testing for whatever reason, and that is fine. That's up to you to find out and decide ; as long as you've made a decision, it means that you've read the list, accepted the price & consequences of (not) testing and are good to go !

If you think about your project, you probably have blinders on. Programmer's or owner's blinders are the worst, because you know what the app is supposed to do and, inevitably, you will test inside those bounds. Users might use your app not in the way you thought they would, and this would be a UX problem. We're here only about testing, making sure that your app works offline, or on low battery, or when denied access rights that you actually need. Some stuff users might do that you took for granted during all these weeks of testing. This is mostly about "thinking outside the box" or, what I like to call it : doing the best job possible as a tester.

Here's a rather famous tweet that illustrates what I mean.

<blockquote class="twitter-tweet" data-lang="en"><p lang="nl" dir="ltr">QA Engineer walks into a bar. Orders a beer. Orders 0 beers. Orders 999999999 beers. Orders a lizard. Orders -1 beers. Orders a sfdeljknesv.</p>&mdash; Bill Sempf (@sempf) <a href="https://twitter.com/sempf/status/514473420277694465?ref_src=twsrc%5Etfw">September 23, 2014</a></blockquote>

It's funny (or at least I like to think it is) and it's true. This simple example illustrates many things to check in your app.

The whole list looks quite overwhelming and that is normal. I want it to be as complete as possible. Like I said earlier, the point is to inform you of the many possibilities. It is up to you to decide if an element is worth testing for your specific case. Wether it is or isn't is your decision, as long as you've made the decision and are aware of it. That is the point of this list. 

-----

### b : Effectively using the list
You can use this list however you like, because as long as you use it you'll improve the quality of the software you're shipping. The fact that you use that list is far more important than how you use that list. It could be a thorough and regular walkthrough, a pre-release checklist, or even as simple as a quick read before going to bed. As long as you read it and know it's there, it'll be useful somehow.

As a quick but very important note, remember that a lot of this testing can be done using classic unit tests, and UI tests. That should already cover the vast majority of the important elements to test. The rest can be tested manually if necessary. That means that you can write test suites and use it in various places in your app to ensure long term stability. **Testing all this manually would be a nightmare** ; if you don't know how to write unit tests or UI tests, look it up. There is a lot to learn there that will save you a tremendous amount of time, money, and avoid the ordeal that manual testing is.

-----

### c : Contributing
I'm mostly writing this alone, the only help/inspiration I got was from browsing the internet (see next chapter, I.d) on various subjects. Sadly, I am limited by my own knowledge and experience, which means there is certainly a lot of content missing in areas that you, dear reader, have a lot of experience in. That's where Github comes in place ; you can freely ask for a pull request, modifying my content or adding your own. I will review it and validate it to the best of my knowledge, probably with the help of the community. Stuff like security, encryption, networking, those are areas where I lack the most. Considering I'm an average Joe, that's probably where most people lack skill, and where your app will be most vulnerable/lacking as well. This means those are areas (the ones you're weak in) must be triple checked and you should definitely spend extra attention on it !

Other ways of contributing / saying thank you would be the following :
- Add a nice comment
- Participate yourself in the improvement of this list
- Like/Star the page
- Share the content using the repo link (please do not copy paste or rehost yourself, link directly)
- If you really want to reward me in some special way, donations are always appreciated and never mandatory.

 After all, I'm spending a lot of time to save you all some time as well, that must be worth something of the above :D

-----

### d : How it all started, thank you
And finally, I would like to thank Michael Hunter for [his amazing checklist](http://www.thebraidytester.com/downloads/YouAreNotDoneYet.pdf "Title"), which inspired me to start my own checklist specifically around mobile development (iOS, Android, Windows Phone). It does look like a lot of time and effort was put into that version of the list, which I know is not even the first version. That is great work and if you're outside of mobile, I **strongly** suggest you go check it out. My only hope is to, someday, achieve a checklist of a similar quality. From there, I found multiple checklists on the internet, most of them very incomplete, but the one that stood out is [David Dias' Front-End checklist](https://github.com/thedaviddias/Front-End-Checklist "Title"), which also inspired me in many ways to improve my own. Please, go check him out as well, it's work worth spreading !

## II : Text Inputs

Text inputs come in many flavours, size and use cases. Obviously you don't treat <code>password</code> fields the same way you treat another field, and there are many fields with many different purposes. This list should cover them all, or at least most of them. Testing your input will be done through multiple aspects. You need to make sure validation works in logic and UI, that the textfield handles all kinds of stress and inputs, and that, if any, the formatting works properly. All those together should ultimately provide you a working textfield.

### a : Text :
You're not done yet if you haven't dealt with all of the following inputs and situations, when validating text inputs. Note that these also apply to most of other input types (password, email, numbers, etc.). If you're dealing with any type of string input, consider the following list as well as the relevant list.

- [ ] Alphanumeric : `aBCd 1234`
- [ ] Symbols / non alphanumeric : `#@ !? ;) $= §`
- [ ] Emojis : all formats : `:grinning:` or `:-)` or 😀 or `U+1F60A`
- [ ] Numerical : `123`
- [ ] Other alphabets : 
	- [ ] Chinese / Arabic / Cyrillic / Turkish : there are some very annoying cases that can be visually hard to find, like [the Turkish I](https://en.wikipedia.org/wiki/Dotted_and_dotless_I)
	- [ ] Most ASCII & non-ASCII characters
- [ ] Escape characters : `\t`, `\"`, ... 
- [ ] Empty : `string.Empty`
- [ ] Null : `null`
- == Your suggestion here ==

-----

You're not done yet if you haven't tried to input data in the following ways :
- [ ] One character at a time from left to right
- [ ] From the end of a partially filled field
- [ ] From the middle of a partially filled field
- [ ] From the start of a partially filled field
- [ ] Pasting invalid characters (try various combinations)
- [ ] Pasting very large inputs of valid/invalid type. (Try various combinations)
- [ ] Pasting valid input
- [ ] Pasting valid input inside partial valid input
- [ ] Pasting valid input inside partial invalid input (the point is to check the state change of validity after the paste)
- == Your suggestion here ==

-----

- [ ] How many characters do you accept ?
- [ ] Did you define what a valid input is (Only letters ? Only numbers ? 3 numbers & 4 letters ?) ?
- [ ] Did you define what an invalid input is ? (Is Empty invalid? Is "valid + spaces" invalid?)
- [ ] Do you deal with invalid inputs ? (Highlight input, display error, something like that)
- [ ] Do you deal with numbers properly ?
	- [ ] Do you deal with zero ?
	- [ ] Do you deal with decimals ?
	- [ ] Do you deal with negative numbers ? 
	- [ ] Do you deal with large numbers ?
- [ ] Do you accept an empty input ?
- [ ] Spaces
	- [ ] Space(s) at the start of the input
	- [ ] Space(s) at the end of the input
	- [ ] Space(s) in the middle of the input
 - == Your suggestion here ==

And that's only for one text input in one screen of your app. You should validate each text input field thoroughly, throughout the app. And this is not even mentioning input formatting, like adding spaces automatically between inputs, or forcing some characters to be coloured or changed to uppercase.

-----

### b : Numbers 
You're not done yet if you have not thoroughly tested all your number inputs with
- [ ] Only zero : `0`
- [ ] Decimals : `13.37` or `13,37`(mind the separator depending on the locale ! )
- [ ] Negative numbers : `-1337`
- [ ] Very large numbers : `10^20`
- [ ] A number bigger than the required range upper limit
- [ ] A number smaller than the required range lower limit
- [ ] A number equal to the upper range limit
- [ ] A number equal to the lower range limit
- [ ] A number as a string : `"124"`
- [ ] A number with different culture decimal points : `12.23` vs `12,23` 
- [ ] A number with separators (and decimals) : `10.234,96` vs `10,234.96`
- [ ] Currencies in various cultures : `13.37 €` vs `€ 13.37`
- [ ] The maximum / minimum number of decimal values
	- [ ] What is the number ?
	- [ ] How do you round it when you have more decimals beforehand ? `13.34` instead of `13.3389`
	- [ ] How do you display it when you don't have enough decimals ? `13.00` or just `13`, or something else entirely?
	- [ ] Are those decimals included in the maximum number limit ? Can I type `4000` but not `3999.99`, or can I also type `4000.56` ?
- [ ] How do you deal with editing / formatting input on the fly?
	- [ ] What happens if you erase the decimals, do you automatically erase the separator?
	- [ ] What happens if you add a separator as the first character? `12345` becomes `0,12345` or `,12345` or something else? Is it reformatted to `0,12` ?
- [ ] Do you handle copy pasting of values into the field ? Try with paste inputs that are
	- [ ] Out of range ( `-1`, `0`, `-1000`, `234940` )
	- [ ] Too big
	- [ ] Too small
	- [ ] Badly formatted
	- [ ] Not numbers
	- [ ] Basically everything from the number list, but in copy paste (multiple characters at once often behaves differently)
- == Your suggestion here ==

-----

### c : Email
You're not done yet if you haven't thoroughly tested all your email inputs with
- [ ] Missing the `@` character
- [ ] Multiple `@` characters
- [ ] Missing the `.` character
- [ ] Most alphanumeric characters
- [ ] All email-friendly symbols ( `.`, `-` , `_`, etc. )
- [ ] Long emails
- [ ] Short emails
- [ ] Empty
- [ ] Invalid emails
	- [ ] Special/invalid characters `ù`, `à`, etc.
	- [ ] Different alphabets (Turkish, Cyrillic)
- == Your suggestion here ==

-----

### d : Telephone
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### e : Password
You're not done yet if you haven't
- [ ] tried copying from the password field and pasting somewhere else
- [ ] hidden the password's field content
- [ ] tested  all cases from previous fields (passwords might contain numbers, letters, and should be valid in all cases)
- == Your suggestion here ==

-----

### f : Date
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### g : Time
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### h : Search
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

## II : Other Inputs

Inputs are not always text in forms, there are other ways people can give their... input. And there are therefore other ways to forget stuff !

### a : Disabled inputs
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### b : Button
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### c : Radio/Checkbox
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### d : Switches
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

## III : Error management

Error management is the pillar of an app in good health. It'll help you track down issues (other tools will help too) and therefore fix bugs. But you don't want that to be an obstacle for your user and their experience of your app. There is a fine balance to achieve between good UX, bug tracking, and notifying the user an issue has arised.


### a : Making errors & exceptions
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### b : Logging errors
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### c : Tracking errors
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

### d : Dislpaying alerts
You're not done yet if
- [ ] CASE
- == Your suggestion here ==

-----

