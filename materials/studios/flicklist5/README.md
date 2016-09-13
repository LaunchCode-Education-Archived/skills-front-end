##### Web Track
[Back to Class 6](../../class6)

# Studio: FlickList 5

In today's (final!) studio, you will add some finishing touches to the project. The changes are mostly cosmetic, but they will require you to refactor a significant chunk of your html and javascript code.

### Demo

Here is a demo of what you are trying to accomplish: <a href="http://htmlpreview.github.io/?https://github.com/LaunchCodeEducation/flicklist/blob/636afdd8442225455cef24ea4a8560705a17313c/index.html" target="_blank">FlickList 5 Demo</a> (note: I noticed some weird behavior with this demo on Safari, so be sure to open it up in Chrome). Play around with the demo for a minute and get familiar with its features. Also, keep the demo open in a separate window, so you can refer to it while working on the assignment.

Note the following additions since last time:
* The proverbial furniture has been rearranged. The two sections (watchlist and browse) are no longer arranged in side-by-side columns; instead the browse section has moved back to its former home, below the watchlist section.
* The browse section is way different. Rather than displaying all the movies at once inside a list, now only one movie is shown at a time. The user can cycle through movies using a fancy UI "carousel", which displays the movie posters along with buttons for sliding back and forth between movies. Each time the carousel slides, the movie title and description update to reflect the newly active movie whose poster has slid into view. 
* The browse section layout uses the Bootstrap grid system, in fact a *nested* grid: At the macro level, the section is split into (A) a column on the left for the movie info and carousel, and (B) a column on the right for the search form. Diving into that first column, it is further subdivided into (A-1) a column on the left for the movie title and overview, and (A-2) a column on the right for the carousel and the "Add to Watchlist" button.


### Starter Code

Same procedure as usual. First, fetch the studio5 branch from upstream:

```nohighlight
$ git fetch upstream studio5
remote: Counting objects: 21, done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 21 (delta 6), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (21/21), done.
From https://github.com/LaunchCodeEducation/flicklist
 * branch            studio5    -> FETCH_HEAD
   74b1223..fe10c4f  studio5    -> upstream/studio5
```

Then, checkout a new local branch:

```nohighlight
$ git checkout -b studio5-my-work upstream/studio5
Branch studio5-my-work set up to track remote branch studio5 from upstream.
Switched to a new branch 'studio5-my-work'
```

### A Brief Tour

Here's what has changed since last time:

##### index.html

The two-column layout has already been removed for you. Notice how the two sections are no longer inside a "row" div, and no longer have class names like "col-md-7", and the "main-content" div no longer has a class of "fluid-container". 

There is some additional code in the script at the bottom of the page. More on that later.

##### flicklist.js

Nothing new here.

##### styles.css

A couple minor changes, not worth talking about.

### Assignment

For this studio, there are some tasks that do not explicitly have TODO comments in the source code (it would be too messy / ambiguous as to where to place the comment). So follow the steps as outlined here:

#### 0. API key

You know what to do.

#### 1. Rearrange to use grid

For starters, let's just try to implement this new grid layout in the browse section. In `index.html`, build out the following structure:

```nohighglight
+-----------------------------------------------------------------------------------------------------+
|                                           Browse Section                                            |
| +-----------------------------------------------------------+ +-----------------------------------+ |
| |         Container A (67% width)                           | |          Container B (33%)        | |
| | +------------------------------+ +----------------------+ | |      (header and search form)     | |
| | |     Conainer A-1 (58%)       | | Container A-2 (42%)  | | |                                   | |
| | |                              | |                      | | |                                   | |
| | +------------------------------+ +----------------------+ | |                                   | |
| +-----------------------------------------------------------+ +-----------------------------------+ |
+-----------------------------------------------------------------------------------------------------+
```

This will involve adding some things, moving some things, and deleting some things. 

Eventually the poster image carousel will live in Container A-2, and over in Container A-1 we will display the title and overview of the the currently visible movie poster. But for now, just ignore that, and implement this scaffolding. 

A few things to point out:
* Note that your search form ("Search by Topic") and header ("Browse Movies") should be placed inside Container B.
* Give Container A-1 an attribute of `id="browse-info"`
* Place A-1 and A-2 inside a Bootstrap <a href="http://getbootstrap.com/components/#wells" target="_blank">well</a> by wrapping the entire row that holds A-1 and A-2 inside a wrapper div with `class="well"`
* Don't be afraid of breaking what you currently have. 
* Google "Bootstrap Grid" if you need a refresher.
* Feel free to open the Studio Demo in your browser and inspect its HTML with the dev tools.

#### 2. Add Some Dummy Data

Next, let's hard-code some fake content into your HTML page. Later you will delete this and use jQuery to add the real content dynamically, but this intermediate step should help clarify how to do that.

In `index.html`, add the following content:
* inside Container A-1, place an `<h4>` element with the text "Twilight", followed by an `<hr/>`, followed by a fake overview paragraph about Twilight. Make sure your overview paragraph is an accurate description of the plot of the movie, jk.
* inside Container A-2, add a placeholder `<img>` (with an "src" equal to "https://pbs.twimg.com/profile_images/378800000576832113/3e69602eab961fd19b89cc65ea9bd2e8.jpeg"), followed by a button that says "Add to Watchlist" and has an attribute of `id="add-to-watchlist"`.

#### 3. Create the Carousel

Now for the fun part: inside Container A-2, create a Bootstrap Carousel. How the heck does one do that? It's essentially just like the other Bootstrap components we've already seen, but more complex, and composed of multiple elements rather than just one. You simply create some elements and wire them up with them the right class and id names and other attributes, and Bootstrap will work behind the scenes to make everything function properly. 

Actually, for this task we are going to need to include Bootstrap's javascript library (we currently only have their CSS). So the first step is to head to <a href="http://getbootstrap.com/getting-started/#download-cdn" target="_blank">the bootstrap site</a> and copy/paste their "Latest compiled and minified JavaScript" into the top of `index.html`.

Now it's time to create the carousel. Check out <a href="http://codepen.io/jesselaunchcode/pen/ZWZyeX" target="_blank">this Codepen example</a> (which I made, and which mirrors exactly what you want to do (make sure you expand the "html" window on Codepen so you don't go insane trying to read from a tiny box)), and also <a href="http://www.w3schools.com/bootstrap/bootstrap_carousel.asp" target="_blank">this W3 Schools example</a> (which has some extra stuff we don't care about, but provides explanations of the various parts, which you should read). 

Build your carousel, and fill it with 3 movie poster images, using posters from the internet <a href="http://sumnersunsettheatre.com/wp-content/uploads/Minions-poster.jpg" target="_blank">like this</a>. Give your carousel an attribute of `id=browse-carousel` Make sure to also include the left and right "data slide" buttons, and make sure they work.

Finally add this rule to your `styles.css` file:

```css
#browse-carousel {
	max-width: 300px;
	margin: auto;
}
```

which will ensure that the carousel does not get annoyingly large, and is centered horizontally in its container.

#### 4. New Model Property

Now that you have the page layout and the carousel all set up, it's time to feed your app the actual movie data. You will do this by refactoring some of your javascript code in `flicklist.js`.

The big change is that we no longer want the browse section to display a *list* of movies. We only want to display one at a time. Our underlying model should still use a list (i.e. `model.browseItems`) because we want to keep track of all the movies and have them around-- it's just that user will only visibily see one at a time. 

This means that our `model` object will need a third property. Not only do we need to keep track of the list of browse items, we also need to keep track of *which item*, at any given moment, is the "active" one on display. 

Add another property to the `model` variable. Name the property `activeMovieIndex`, and set it equal to `0`. This number represents which item from the browseItems array is currently active. So for example, because we start off with `0`, this means the first item in the array is the active movie.

##### 5. Refactor the render Function

The old `render` function, when adding the content to the browse section, iterates over each item in `model.browselist`. This doesn't really make sense anymore since we only want to display one browse item at any given time.

##### 5a. Delete the old Code!

Go ahead and delete this whole block of code:

```js
model.browseItems.forEach(function(movie) {
  ...
});

```

Gasp! (Actually, just comment it out. But cut and paste it to the bottom of the file or somewhere else out of the way.)


##### 5b. Figure out the Current Active Movie

Now let's get started building a fresh implementation of displaying the browse section. You should still be inside the `render` function, in the same place where the dust is still settling from decimating the old code.

First, we will need to know which movie object is the currently active one. Make a variable:

```js
var activeMovie =   // TODO fill this in
```

and give it the correct value. (Remember, you have a list of browse items, and you have a number telling you which index is the active index).

##### 5c. Title and Overview

Next, replace the hard-coded "Twilight" content with the actual title and overview for the currently active movie. (Remember, you gave the container an id of "browse-info".)


##### 5d. Revive the "Add to Watchlist" Button

Previously we created a new button for each browse item, but now we just have one permanent button which you have already added to the HTML page. But that button doesn't work and is ugly. Bring it back to life!

Your old code looked like this:

```js
var button = $("<button></button>")
   .text("Add to Watchlist")
   .attr("class", "btn btn-primary")
   .click(function() {
     model.watchlistItems.push(movie);
     render();
   })
   .prop("disabled", model.watchlistItems.indexOf(movie) !== -1);
```

You pretty much want to do all that same stuff here. The only difference is that instead of *creating a new button* and storing it in a variable, you just need to modify the existing button (Remember, you gave it an id attribute).

##### 5e. Fill the Carousel

Now let's fill the carousel with movie poster images. Here's some starter code:

```js
// fill carousel with posters
var posters = model.browseItems.map(function(movie) {
 // TODO 
 // return a list item with an img inside  
});
$("TODO").append(posters);
```

As you can see, we are mapping over the browseItems to create an array of elements. Then we are appending those elements into the carousel. 

Inside the `map` callback, you should break that down into two steps: first, create a poster image (you can look up to remember how you did that in the watchlist), and then append it into an `<li>`. Remember, your `<li>` needs to have a special class name of `"item"` in order for the Bootstrap carousel to recognize it.

You also must fill in that jQuery selector to make sure you are appending the list items into the apropriate place.

##### 5f. Activate the Correct Poster Item

The carousel also requires that exactly one list item also has a class of `"active"`.

Here's a freebie:

```js
posters[model.activeMovieIndex].addClass("active");
```

Just add the above line. But don't paste it, type it out yourself!

##### 6. Respond to Carousel Sliding

Your page should now have a working carousel with actual movie data in it. 

There is still one bug, which is that whenever the carousel slides to show a new movie poster, the rest of the app fails to respond. The title, overview, and everything else continue to show the previous movie.

To solve this problem we must, actively respond whenever the carousel has slid to a new movie. We have already started this for you in the script at the bottom of `index.html`:

```js
$("#browse-carousel").on("slid.bs.carousel", function() {
   console.log("the carousel just slid!");
   var newIndex = $("#browse-carousel").find(".active").index();
   // TODO 
   // update the model and then re-render
});
```

This code block uses a jQuery function called `on` which allows us to register a callback that will be executed whenever a certain event happens. In our case the event is the carousel sliding, which Bootstrap makes available under the name "slid.bs.carousel". This is just like a normal button with a `click` handler, but the `on` function lets you specify any event, not just a click. In fact, you actually can use `on` with buttons. The following two code blocks are equivalent:

```js
$("#mybutton").on("click", function() {
   console.log("somebody clicked my button!");
});
```

```js
$("#mybutton").click(function() {
   console.log("somebody clicked my button!");
});
```

Anyway, whenever the carousel has slid to a new position, that annonymous function will be executed. We've left a TODO in there for you. The goal is to update the model (remember that your model must keep track of the current active movie index), and then re-render everything. In the line above the TODO, we've already done the hard part of figuring out what the new carousel index is, by using some new jQuery functions, `find` and `index`, whose purpose you can hopefully infer from their usage here.

Once you've got this working, your page should update its content whenever the carousel slides!

##### 7. CSS

The last step is to add some CSS and make everything look tidy. No guidance on this one! You got this. Just compare your version to the demo and rig up some CSS rules to make it work.

One hint, regarding your carousel: remember that a `<ul>`, by default, has some padding on the left side.

### How to Submit

As usual, commit your work on Git and push to a new branch on your GitHub repo. Then, submit a link to your repo on Vocareum.

##### Commit and Push

If you run the `git status` command, you should see that you now have *unstaged* changes:

```nohighlight
$ git status
On branch studio5-my-work
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
      
        modified:   css/styes.css
        modified:   index.html
        modified:   js/flicklist.js

no changes added to commit (use "git add" and/or "git commit -a")
```

We can stage these changes with the `add` command:

```nohighlight
$ git add --all
```

The `--all` adds all of the unstaged files, so you don't have to type them one by one.

If you check your status again now, you should see:

```nohighlight
$ git status
On branch studio5-my-work
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
        modified:   css/styes.css
        modified:   index.html
        modified:   js/flicklist.js
```

All the files are now staged for committing. Go ahead and make a commit, using the -m flag to remind your future self (and others looking at your code) what changes you made during this commit:

```nohighlight
$ git commit -m "finish FlickList 5 studio"
[studio2-my-work 46db232] finish FlickList 5 studio
 2 files changed, 2 insertions(+), 2 deletions(-)
```

The convention is to write your commit messages using the present tense rather than past tense (e.g. "finish" rather than "finished").

If you check your status one more time, you should see this:

```nohighlight
$ git status
On branch studio5-my-work
nothing to commit, working directory clean
```

Finally, *push* your changes to your remote repo:

```nohighlight
$ git push origin studio5-my-work
Counting objects: 62, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (20/20), done.
Writing objects: 100% (22/22), 2.36 KiB | 0 bytes/s, done.
Total 22 (delta 6), reused 0 (delta 0)
To https://github.com/jharvard/flicklist.git
 * [new branch]      studio5-my-work -> studio5-my-work
```

If you go back and revisit github.com/jharvard/flicklist, you should now see your new branch up there! Specificially, near the top-left of the screen, you should see a dropdown menu that says "Branch: master". Click that dropdown and you should see an option for "studio2-my-work". Click on that branch, and you should now see the code you just worked on. Copy the current url in your browser's address bar (you are about to paste that url into Vocareum).

##### Submit on Vocareum

On Vocareum, click the assignment titled **Studio: FlickList 5**. In your `/work` directory you should see a file called `studio5.txt`. Open up this file and fill in the link to your work on GitHub.


#### Publish your Work using Github Pages!

Lastly, let's put your work on display so you can show it off! Github has a feature called Github Pages, which makes it really easy to host your front-end projects on the real, live internet. You simply need to give your repository a branch with with the special name "gh-pages". 

Let's do that now. First, create the new branch locally:

```nohighlight
$ git checkout -b gh-pages
Switched to a new branch 'gh-pages'
```

(Notice that we didn't specify where the new branch should copy from, so by default it used the current studio5-my-work branch, which is what we want).

Now we want to push this branch up to your remote repository. There is one slight complication, which is that when you forked our LaunchCodeEducation/flicklist repo back in Studio 0, your fork also received all of our branches, including our own gh-pages branch. So your remote in fact already has a (out of date) gh-pages branch. So first, delete that one:

```nohighlight
$ git push --delete origin gh-pages
To https://github.com/jharvard/flicklist.git
 - [deleted]         gh-pages
```

and now you can then push this local one:

```nohighlight
$ git push origin gh-pages
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 686 bytes | 0 bytes/s, done.
Total 5 (delta 1), reused 0 (delta 0)
To https://github.com/jharvard/flicklist.git
 * [new branch]      gh-pages -> gh-pages
```

Now you (or anyone) can view your project! Just visit this url http://jharvard.github.io/flicklist (where jharvard is your username).
