
# Now What?

As we wrap up the Skill Track, you may be finished with your coursework, or you may still be working. In either case, the goal of this page is to give you some guidance as to what comes next.

Once you have finished all your coursework, there are two things you should do right away:

1. Get started on a personal project of your own.

2. If you have not already filled out your [Apprenticeship Application][application], go do it!

    *Now?*

    Right now!

    *But I don't feel ready. I haven't even started my project...*

    Seriously, it's okay. You should think of your application process as something you do concurrently while working on your project, rather than something you do after you have finished a perfect project. Once you are in our system as someone who is actively looking for an apprenticeship, we will be able to give you more direct feedback and guidance on what you specifically need to work on (if anything), and you will be linked in to additional programs to get mentorship on your project, or help with your interview skills, or whatever else you need. Filling out the application is simply your way of poking us and saying *Hey LaunchCode, I want a job! This is where I'm currently at. Tell me what I should do next.* So go [poke us right now][application]. It is the most effective step you can take to dramatically expedite your job search.

[application]: https://www.launchcode.org/candidates/applications/new

With that out of the way, let's now talk about front-end development.

## The Frenetic State of Front-end Web Development Today

Finishing this front-end skill track is rather similar to your high school or college graduation, in that you are about to leave the school's bubble and enter The Real World.

And folks, it is a [mad][js-2016-sarcastic], [mad][js-2016-survey] world out there.

Today's font-end ecosystem is a chaotic jungle, teeming with a proliferation of competing standards, frameworks, and tools, and other tools to help you use the tools....

So, two things to keep in mind:

1. In order to get a LaunchCode apprenticeship, your project **does not need** to use any of these cooler fancier technologies. If you just want to make a jQuery app that looks nice and manages some data, that's great.
2. Ultimately, a simple jQuery setup can't support a "real" Javascript app. Eventually, whether it is now, or on the job, you will step foot in some corner of The Jungle. When that happens, the biggest thing to remember is: don't let the insanity intimidate you. Coding is hard, but it's not *that hard*. The complexity of the jungle is mostly [incidental complexity][incidental-complexity], rather than essential.

[js-2016-sarcastic]: https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f#.rob2x09wl
[js-2016-survey]: http://stateofjs.com/
[incidental-complexity]: https://vibratingmelon.com/tag/incidental-complexity/


## Your Project

You should now be in a position where you can, with some effort and some help, create a front-end project similar to the FlickList site we made in class, or the Word Up assignment, or the Apartment Moving site from the Udacity AJAX course.

If you're struggling to think of an idea, here is a basic framework that you can use:

Build some kind of front-end for displaying data from a publicly available API(s). Give the user a fun, interesting, or useful way of exploring and interacting with the content from the API.

But if you have some other idea that doesn't fit this template, then that's great! Go for it, and reach out for any help you need.

## Skills to Improve On

If you want to learn more stuff, here are some directions you could go in:

#### Javascript

Stuff we didn't really talk about:
* [Object-oriented javascript](http://eloquentjavascript.net/06_object.html)
* [Breaking your code up into modules](http://eloquentjavascript.net/10_modules.html)
* Managing [callback hell](http://callbackhell.com) with and without using [Promises](http://blog.parse.com/learn/engineering/whats-so-great-about-javascript-promises/)
* [Regular Expressions](http://eloquentjavascript.net/09_regexp.html)

#### CSS and Design

Stuff we didn't really talk about:
* CSS Layout frameworks like <a href="http://flexbox.io" target="_blank">Flexbox</a> or <a href="https://gridstylesheets.org" target="_blank">Gride Stylesheets</a>
* CSS Preprocessors like <a href="http://lesscss.org">LESS</a> and <a>SASS</a>
* [Material Design][material-design] is a set of graphic design principles set forward by Google. CSS frameworks such as [Materialize CSS][materialize] and [Material Design Lite][mdl] are similar to Bootstrap and make it easy to quickly give your app the Material Design look and feel. Also, check out this [Material version of FlickList][material-flicklist], courtesy of LaunchCode mentor Anthony Stark!

I generally recommend these resources for learning HTML and CSS
* <a href="http://learn.shayhowe.com/html-css/" target="_blank">Shay How</a>


[material-design]: https://material.google.com
[materialize]: http://materializecss.com
[mdl]: https://getmdl.io
[material-flicklist]: http://anthonystark.com/flicklist/

#### A Javascript Framework

As your project grows from 500 lines of code to 5,000 to 50,000, it becomes exponentially harder to "manage the complexity". Every time you try to add a new feature you end up breaking 5 things.

A framework is some technology that provides "scaffolding" around which you can build a project. The idea is that this scaffolding will help / force you into a project architecture that stays maintainable as it grows.

Some popular frameworks are:
* <a href="https://angularjs.org" target="_blank">AngularJS</a>
* <a href="https://facebook.github.io/react/" target="_blank">ReactJS</a> (technically is <a href="http://blog.andrewray.me/reactjs-for-stupid-people/" target="_blank">not exactly a framework</a> by itself)
* <a href="http://emberjs.com" target="_blank">EmberJS</a>

Some less popular (but much better, in my own hipster opinion) frameworks are:
* <a href="https://elm-lang.org" target="_blank">Elm</a> (This is actually an entirely different language that compiles to Javascript)
* [Redux][http://redux.js.org]
* [Cycle][https://cycle.js.org]

This site, <a href="http://todomvc.com" target="_blank">TodoMVC</a> shows you how to build the same Todo List app in a variety of different frameworks.

#### Build-Tools and Stuff

e.g. NPM, Gulp, Webpack...

We're not even gonna go there on this. Feel free, if you're interested, to research this on your own, and we're happy to help with questions you have.

## Ways that FlickList could be extended

Just to help give you more of an idea of the types of things a project can have:

* Improve the movie browsing. The API has tons of data that we aren't using, like movie genres, reviews, actors and actresses. Add more features to help the user browse. This will involve making more API calls and presenting the data in various ways.
* Handle Errors! When our AJAX calls fail to get a response back, our app should handle the failure gracefully, rather than just crap out.
* Add some advanced Javascript features like Promises, wrapping your code in a module(s) and so on.
* Use some advanced CSS technologies like Sass or Less, and Flexbox. Add some nice UI touches like responding to mouse hovers to provide a great user experience.
