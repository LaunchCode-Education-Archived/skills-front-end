##### [Web Track](../..)

# Now What?

Congratulations on finishing the class! Your next step is to make a personal project of your own.

### Project

You should now be in a position where you can (with some struggles and help along the way) create a front-end project similar to the FlickList site we made in class, or Problem Set 8 from CS50.

If you're struggling to think of an idea, here is a basic framework that you can use:

Like FlickList and Pset8, build some kind of front-end for displaying data from a publicly available API. Give the user a cool, fun, or useful way of exploring and interacting with the content from the API. 

### Skills to Improve On

#### Javascript

Stuff we didnt really talk about:
* <a href="https://www.udacity.com/course/object-oriented-javascript--ud015" target="_blank">object-oriented Javascript</a>
* <a href="http://eloquentjavascript.net/10_modules.html" target="_blank">modules</a>
* Managing <a href="http://callbackhell.com" target="_blank">callback hell</a> with and without using a cool JS feature called <a href="http://blog.parse.com/learn/engineering/whats-so-great-about-javascript-promises/" target="_blank">Promises</a>

I generally recommend these resources for learning more Javascript:
* <a href="https://eloquentjavascript.net" target="_blank">Eloquent Javascript</a>
* <a href="https://www.freecodecamp.com" target="_blank">FreeCodeCamp</a>

##### CSS

Stuff we didn't really talk about:
* CSS Preprocessors like <a href="http://lesscss.org">LESS</a> and <a>SASS</a>
* CSS Layout frameworks like <a href="http://flexbox.io" target="_blank">Flexbox</a> or <a href="https://gridstylesheets.org" target="_blank">Gride Stylesheets</a>

I generally recommend these resources for learning HTML and CSS
* <a href="http://learn.shayhowe.com/html-css/" target="_blank">Shay How</a>


##### A Javascript Framework

As your project grows from 500 lines of code to 5,000 to 50,000, it becomes exponentially harder to "manage the complexity". Every time you try to add a new feature you end up breaking 5 things. 

A framework is some technology that provides "scaffolding" around which you can build a project. The idea is that this scaffolding will help / force you into a project architecture that stays maintainable as it grows. 

Some popular frameworks are:
* <a href="https://angularjs.org" target="_blank">AngularJS</a>
* <a href="http://emberjs.com" target="_blank">EmberJS</a>
* <a href="https://facebook.github.io/react/" target="_blank">ReactJS</a> (technically is <a href="http://blog.andrewray.me/reactjs-for-stupid-people/" target="_blank">not exactly a framework</a> by itself)
* <a href="https://elm-lang.org" target="_blank">Elm</a> (this is actually an entirely new language that compiles to Javascript. You won't find a lot of jobs in Elm (yet...), but it's highly enjoyable (a personal favorite of mine) and quite possibly a much better way of writing web apps, time will tell)

This site, <a href="http://todomvc.com" target="_blank">TodoMVC</a> shows you how to build the same Todo List app in a variety of different frameworks.


### Ways that FlickList could be extended

* Add a backend. Currently users don't actually get to save their watchlist, which kind of defeats the whole purpose of the thing. You could create full site with a back-end and a database to persist user changes. I reccomend you start with something like the Greetings studio and build from there, adding user logins and accounts. Use Pset 7 as a reference point. Then add in your FlickList code. The other nice thing about adding a back-end is that technically we've been doing a slighly insecure thing -- hard-coding our API key directly into the Javascript file. This code runs on the user's machine, so it would not be difficult for users to steal our API key. A better way to interact with an API is to set up your own back-end as a "middle-man": so for example flicklist.js makes a request to discoverMovies.php which makes a request to TheMovieDB's API. In Pset 8 you can see an example of how this is done.
* Add some advanced Javascript features like Promises, wrapping your code in a module and so on.
* Use some advanced CSS technologies like Sass or Less, and Flexbox. Do some fancy stuff like responding to mouse hovers to provide a great user experience.
* Improve the movie browsing. The API has tons of data that we aren't using, like movie genres, reviews, actors and actresses. Add more features to help the user browse. This will involve making more API calls and presenting the data in various ways.
* Handle Errors! When our AJAX calls fail to get a response back, our app should handle the failure gracefully, rather than just crap out.
