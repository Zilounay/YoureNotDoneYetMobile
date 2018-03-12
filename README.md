# You're Not Done Yet - Mobile

## Table of Contents

//This is more of a TODO list more than anything right now
1. Intro
2. Text Inputs
3. Other Inputs (checkbox, switches, mutually exclusive controls)
3. Error Management
4. Navigation (push, pop, tabs, modal)
8. Background (saved state, springboard card)
5. Connectivity
6. Localization (of text & images)
7. Interruptions (calls)
9. Storage
10. Security
11. Accessibility (software buttons, zooming, font sizes, text to speech, ...)

## I : Intro

What is this about ? This is about testing your app thoroughly and completely. This list will include as many elements as possible that you should test. Many of which you probably have already tested, some that you might have not thought about. This is about checking all the boxes and either validate the fact that you did indeed test X & Y, but that you also decided to ignore Z. Many of the elements of the checklist might not apply to you, because your app does not have that specific feature or does not use a specific technology. You might also simply want to skip some of testing for whatever reason, and that is fine. That's up to you to find out and decide ; as long as you've made a decision, it means that you've read the list, accepted the price & consequences of (not) testing and are good to go !

If you think about your project, you probably have blinders on. Programmer's or owner's blinders are the worst, because you know what the app is supposed to do and, inevitably, you will test inside those bounds. Users might use your app, not in the way you thought they would, and this would be a UX problem. We're here only about testing, making sure that your app works offline, or on low battery, or when denied access rights that you actually need. Some stuff users might do that you took for granted during all these weeks of testing. This is mostly about "thinking outside the box" or, what I like to call it : doing the best job possible as a tester.

Here's a rather famous tweet that illustrates what I mean.

<blockquote class="twitter-tweet" data-lang="en"><p lang="nl" dir="ltr">QA Engineer walks into a bar. Orders a beer. Orders 0 beers. Orders 999999999 beers. Orders a lizard. Orders -1 beers. Orders a sfdeljknesv.</p>&mdash; Bill Sempf (@sempf) <a href="https://twitter.com/sempf/status/514473420277694465?ref_src=twsrc%5Etfw">September 23, 2014</a></blockquote>

It's funny (or at least I like to think it is) and it's true. This simple example illustrates many things to check in your app :
- Input validation :
  - Do you accept alphanumeric characters only ?
  - Do you accept symbols / non alphanumeric characters ?
  - Do you deal with Chinese / Arabic / Cyrillic AND Turkish alphabets ?
  - How many characters do you accept ?
  - Do you accept only letters ?
    - Did you define what a valid input is ?
    - Did you define what an invalid input is ?
    - Do you deal with invalid words ?
  - Do you accept only numbers ?
    - Do you accept zero ?
    - Do you accept decimals ?
    - Do you accept negative numbers ? 
    - Do you accept large numbers ?
 - Do you accept an empty input ?
 - What happens if I paste 100 characeters in it ? Of various invalid/valid input types.
 - Many more...

And if you've dealt with all that, you still have to think about error management, probably some input formatting (like adding a comma if you're okay with decimals), and then you'd still have some work to do. And that's only for one text input in one screen of your app. There is a lot more.

It can look quite overwhelming and that is normal. I want this list to be as complete as possible. Like I said earlier, the point of this list is to inform you of the many possibilities. It is up to you to decide if an element is worth testing for your specific case. Wether it is or isn't is your decision, as long as you've made the decision and are aware of it. That is the point of this list. 

You can use this list however you like, because as long as you use it you'll improve the quality of the software you're shipping. The fact that you use that list is far more important than how you use that list. It could be a thorough and regular walkthrough, a pre-release last minute checklist, or even as simple as a quick read before going to bed. As long as you read it and know it's there, it'll be useful somehow.

And finally, I would like to thank Michael Hunter for [his amazing checklist](http://www.thebraidytester.com/downloads/YouAreNotDoneYet.pdf "Title"), which inspired me to start my own checklist specifically around mobile development (iOS, Android, Windows Phone). It does look like a lot of time and effort was put into that version of the list, which I know is not even the first version. That is great work and if you're outside of mobile, I **strongly** suggest you go check it out. My only hope is to, someday, achieve a checklist of a similar quality.


