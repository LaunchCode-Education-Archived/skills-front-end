
# Now What?

Congratulations on finishing the class! Your next step is to make a personal project of your own.

## The Frenetic State of Front-end Web Development Today

This is kind of like high school or college graduation, where are about to leave the school's bubble and enter The Real World.

And folks, it is a [mad][js-2016-sarcastic], [mad][js-2016-survey] world out there.

Today's ecosystem is a chaotic jungle, teeming with a proliferation of competing standards, frameworks, and tools, and other tools to help you use the tools....

Two things to keep in mind:

1. In order to get a LaunchCode apprenticeship, your project **does not need** to use any of these cooler fancier technologies. If you just want to make a jQuery app that manages some data, that's fine.
2. Ultimately, a simple jQuery setup can't support a "real" javascript app. Eventually, whether it is now, or on the job, you will step foot in some corner of The Jungle. When that happens, the biggest thing to remember is: don't let the insanity intimidate you. Coding is hard, but it's not *that hard*. The complexity of the jungle is mostly [incidental complexity][incidental-complexity], rather than essential.

[js-2016-sarcastic]: https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f#.rob2x09wl
[js-2016-survey]: http://stateofjs.com/
[incidental-complexity]: https://vibratingmelon.com/tag/incidental-complexity/


## Your Project

You should now be in a position where you can (with some struggles and help along the way) create a front-end project similar to the FlickList site we made in class, or the Apartment Moving site from the Udacity AJAX course.

If you're struggling to think of an idea, here is a basic framework that you can use:

Like FlickList or the Apartment Moving site, build some kind of front-end for displaying data from a publicly available API(s). Give the user a fun, interesting, or useful way of exploring and interacting with the content from the API.

But if you have some other idea that doesn't fit this template, then that's great! Go for it, and reach out for any help you need.

## Skills to Improve On

If you want to learn more stuff, here are some directions you could go in:

#### Javascript

Stuff we didn't really talk about:
* [Object-oriented javascript](http://eloquentjavascript.net/06_object.html)
* [Breaking your code up into modules](http://eloquentjavascript.net/10_modules.html)
* Managing [callback hell](http://callbackhell.com) with and without using [Promises](http://blog.parse.com/learn/engineering/whats-so-great-about-javascript-promises/)
* [Regular Expressions](http://eloquentjavascript.net/09_regexp.html)

#### CSS

Stuff we didn't really talk about:
* CSS Layout frameworks like <a href="http://flexbox.io" target="_blank">Flexbox</a> or <a href="https://gridstylesheets.org" target="_blank">Gride Stylesheets</a>
* CSS Preprocessors like <a href="http://lesscss.org">LESS</a> and <a>SASS</a>

I generally recommend these resources for learning HTML and CSS
* <a href="http://learn.shayhowe.com/html-css/" target="_blank">Shay How</a>

#### A Javascript Framework

As your project grows from 500 lines of code to 5,000 to 50,000, it becomes exponentially harder to "manage the complexity". Every time you try to add a new feature you end up breaking 5 things.

A framework is some technology that provides "scaffolding" around which you can build a project. The idea is that this scaffolding will help / force you into a project architecture that stays maintainable as it grows.

Some popular frameworks are:
* <a href="https://angularjs.org" target="_blank">AngularJS</a>
* <a href="https://facebook.github.io/react/" target="_blank">ReactJS</a> (technically is <a href="http://blog.andrewray.me/reactjs-for-stupid-people/" target="_blank">not exactly a framework</a> by itself)
* <a href="http://emberjs.com" target="_blank">EmberJS</a>
* <a href="https://elm-lang.org" target="_blank">Elm</a> (this is actually an entirely new language that compiles to Javascript. You won't find a lot of jobs in Elm (yet...), but it's highly enjoyable (a personal favorite of this writer's) and probably a much better way of writing web apps.)

This site, <a href="http://todomvc.com" target="_blank">TodoMVC</a> shows you how to build the same Todo List app in a variety of different frameworks.

#### Build Tools and Stuff

e.g. NPM, Gulp, Webpack...

We're not even gonna go there on this. Feel free, if you're interested, to research this on your own, and we're happy to help with questions you have.

## Ways that FlickList could be extended

Just to help give you more of an idea of the types of things a project can have:

* Improve the movie browsing. The API has tons of data that we aren't using, like movie genres, reviews, actors and actresses. Add more features to help the user browse. This will involve making more API calls and presenting the data in various ways.
* Handle Errors! When our AJAX calls fail to get a response back, our app should handle the failure gracefully, rather than just crap out.
* Add a backend. Currently users don't actually get to save their watchlist, which kind of defeats the whole purpose of the thing. You could create full site with a back-end and a database to persist user changes. I reccomend you start with something like the Greetings studio and build from there, adding user logins and accounts. Use Pset 7 as a reference point. Then add in your FlickList code. The other nice thing about adding a back-end is that technically we've been doing a slighly insecure thing -- hard-coding our API key directly into the Javascript file. This code runs on the user's machine, so it would not be difficult for users to steal our API key. A better way to interact with an API is to set up your own back-end as a "middle-man": so for example flicklist.js makes a request to discoverMovies.php which makes a request to TheMovieDB's API. In CS50's Pset 8 you can see an example of how this is done.
* Add some advanced Javascript features like Promises, wrapping your code in a module(s) and so on.
* Use some advanced CSS technologies like Sass or Less, and Flexbox. Do some fancy stuff like responding to mouse hovers to provide a great user experience.
