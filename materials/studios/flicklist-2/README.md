##### Web Track
[Back to Class 2](../../class2)

# Studio: FlickList 2

Today we will add a hodge-podge of miscellaneous new features to our movie site. We'll include some CSS to apply styles to the page, and build on our interaction with the API. 

Along the way, hopefully you will continue to get more comfortable with jQuery, CSS, AJAX, making API calls, and working with HTML forms.

### Demo

Here is a demo of what you are trying to accomplish: <a href="http://htmlpreview.github.io/?https://github.com/LaunchCodeEducation/flicklist/blob/f3dae711763c73f56267ac35e076c56383183829/index.html" target="_blank">FlickList 2 Demo</a>. Play around with the demo for a minute and get familiar with its features. Also, keep the demo open in a separate window, so you can refer to it while working on the assignment.

Note the following additions since last time:
* In the browse list, each movie is accompanied by a paragraph summarizing its plot.
* Once the user clicks the "Add to Watchlist" button for a movie, the button then becomes disabled, preventing the same movie from being added more than once.
* In the watchlist, each movie is represented by an orange rectangle. These rectangles line up next to each other from left to right, without skipping down to a new line until they run out of space on the right-hand side of their container.
* The page has some styles and is a little prettier than before.
* At the top of the browselist, there is a search bar which users can use to search for particular movies. Upon submitting the form, the browse list repopulates full of movies with matching titles.

### Git Yer Hands on the Starter Code

Same procedure as usual here. First, fetch the studio2 branch from upstream:

```nohighlight
$ git fetch upstream studio2
remote: Counting objects: 21, done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 21 (delta 6), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (21/21), done.
From https://github.com/LaunchCodeEducation/flicklist
 * branch            studio2    -> FETCH_HEAD
   74b1223..fe10c4f  studio2    -> upstream/studio2
```

Then, checkout a new local branch:

```nohighlight
$ git checkout -b studio2-my-work upstream/studio2
Branch studio2-my-work set up to track remote branch studio2 from upstream.
Switched to a new branch 'studio2-my-work'
```

### A Brief Tour

Our project now looks like this:

```nohighlight
$ tree
.
├── css
│   └── styles.css
├── index.html
└── js
    └── flicklist.js
```

Notice the new directory, `css`, which contains a stylesheet, `styles.css`. 

Let's look briefly at each of our files:

##### index.html

The HTML file has only changed slightly since we last left it:
* In the `<head>` there is now a link to our stylesheet. 
* In the browse section, we have a TODO, asking you to create a `<form>` for the user to search for movies
* At the bottom, we have a `<script>` tag inside of which is some partially completed JS code with some more TODOs. This is where you will specify what the form should do when the user clicks the submit button.

##### flicklist.js

Our javascript file is also pretty similar to last time, with just a few changes:
* There is a new function, `searchMovies`, which will be invoked as part of the submit handler on the form (see above). The body of this function is pretty empty (so far!).
* The `render` function has a few TODOs for you.

Also notice inside `render` that we have re-written some of the jQuery code in a style that might seem a little funny. For example, this line:

```js
var button = $("<button></button>")
   .text("Add to Watchlist")
   .click(function() {
     model.watchlistItems.push(movie);
     render();
   });
```

or this one:

```js
var itemView = $("<li></li>")
   .append($("<hr/>"))
   .append(title)
   .append(button);
```

This is a common style for lines of code in which you are chaining together a bunch of jQuery method calls one after the other. When these chains become long enough, there comes a point where they will annoyingly run off the right edge of the screen. To mitigate that, the convention is to place each subsequennt method call on its own new line, indented once.

##### styles.css

Finally, open up the new stylesheet. As you can see, we've already gotten started applying some styles to the page.

As a quick exercise, go preview the page in your browser right now, and open up Dev Tools. In the Elements tab, notice that one of the things you can inspect is the styles of your elements. You can even change the styles and see the results immediately! Spend a minute playing and tinkering with the styles we have added.

### Assignment

Work your way through the TODOs in the source code. The tasks are numbered. You should work on them in the order prescribed, as follows:

##### 0. API key

As usual, add your api key to the object near the top of `flicklist.js`.

##### 1. Add a Description Paragraph to Each Browselist Item

On the browse list, let's spice up those list items by displaying some more data about the movies. Using jQuery, create a `<p>` with a description of the movie's plot. You can find this description as a string somewhere inside the movie object. Just as the title is accessbile via the property `movie.original_title`, the description is a different property. What's the name of the property? You'll have to use a `console.log` statement to poke around and find out. (It's not `movie.description`). Once you have created the paragraph, append it to `itemView` below the title and above the "Add to Watchlist" button.

##### 2. Disable Buttons

Next, implement this feature: an "Add to Watchlist" button should be disabled if the movie in question is already present in the user's watchlist. 

To determine whether the movie is already present, you can use the javascript array function `indexOf`, which returns the index of a thing in an array, unless the thing is not found, in which case `-1` is returned. For example:

```js
var nums = [0, 7, 5, 2];
nums.indexOf(5) // returns 2
nums.indexOf(5000) // returns -1
```

To disable the button, you can use jQuery's `prop` function, e.g.
```js
var nuclearReactor = $("#nuclear-reactor");
nuclearReactor.prop("disabled", true);
```

Once you have this working, take a quick note of the CSS rule we used in order to achive the visual effect. We lower the `opacity` property (in otherwords, transparency) of disabled buttons. In order to select for only disabled buttons, we used the `:disabled` <a href="http://www.w3schools.com/css/css_pseudo_classes.asp" target="_blank">pseudoclass</a>.

##### 3. Give Watchlist Items a Class Attribute

Next, it's time to apply some styles to thosewatchlist `<li>`s, so that they are big orange bricks. But first, in order to do that, we'll need to give them a `class` attribute, so that our CSS can select them. Inside the `render` function, within the `forEach` iteration over `model.watchlistItems`, use the jQuery `attr` function to give the `itemView` variable a class of `"item-watchlist"`.

Verify that you succeeded as follows: In your browser window, add some movies to the watchlist. Then, open up the dev tools, go to the Console tab, and type this:

```js
$(".item-watchlist")
```

followed by the Enter key. You should see an array with some `<li>`s inside it, one for each watchlist item! You should not see an empty array, i.e. `[]`.

##### 4. Style the Watchlist Items as Orange Bricks

Now that your watchlist items have a class attribute, you can apply styles to them. Open up `styles.css`, and create a new class selector for elements with the class "item-watchlist" (hint: CSS selectors are the same as jQuery selectors). Add some styles until your watchlist tiems resemble those orange bricks from the demo. One style you'll definitely want to apply is:

```css
display: inline-block;
```

This is what enables that left-to-right flow pattern. (See this <a href="http://stackoverflow.com/questions/8969381/what-is-the-difference-between-display-inline-and-display-inline-block" target="_blank">Stack Overflow post</a> for a nice overview of the differences between `block`, `inline`, and `inline-block`).

You'll also need to apply a few other styles: a lot of padding, a little bit of margin on <a href="http://stackoverflow.com/questions/356759/a-mnemonic-for-the-order-of-css-margin-and-padding-shorthand-properties" target="_blank">just the right and bottom edges</a>, and the colors obviously need to change.

##### 5. Change the Text Color to Gray

Next, create a css rule that will set a baseline default of gray for the color of all text in the body of the document. To accomplish this, you only have to make one rule! you don't have to go and start adding declarations to each and every selector in the CSS file. You simply have to apply the style to some common container, and then all descendants of the container will automatically inherit the same style.

##### 6. Add a Form to the Page

The last new feature we need to add is a `<form>`, with a text field and a submit button, via which users can search for particular movies. 

The first step to implementing this feature is simply to add the form to `index.html`. Go ahead and do that now. Your form does not need any of the usual attributes, like `action` or `method`, because we are going to intercept and cancel its submit event anyway. The one attribute you should give the form is an `id` equal to `"form-search"`. Inside the form, you should have two `<input>`s: one, a text field, and the other, a submit button.

##### 7. Style the Buttons

Very briefly, let's jump back over to `styles.css` and apply some styles to the buttons, both the "Add to Watchlist" buttons and the "Search by Title" submit button on the form

Notice how the selector here includes `input[type=submit]` in order to select for both normal buttons and submit buttons on forms.

##### 8. Add a Submit Handler to the Form

Once your form is present on the page, the next step is to give it a submit handler. We want to specify that when the user presses the submit button, the `searchMovies` function (which you will implement next) gets invoked, using the search term that the user typed in, with `render` as the callback to be executed after receiving a response from the api.

As you can see, we use jQuery's `.submit` function, which is very similar to `.click` in that it allows you to pass in a function to be executed whenever a form is submitted. You must:
* A: fill in the jQuery selector so that we are calling `.submit` on our form
* B: within the submit handler function, fill in another jQuery selector to figure out what the user typed into the search bar. For this task you must use a selector very similar to the example in `styles.css` for the submit button (`input[type=submit]`).
* C: also within the body of the submit handler function, invoke the `searchMovies` function and pass in the arguments it needs.

If you've done everything correctly you should be able to see some output on the console. Search for "cocounut" and you should see a log statement that reads: "searching for movies with 'coconut' in their title...".

##### 9. Implement the `searchMovies` Function

Finally, let's implement this function in `flicklist.js`. As a starting point, you can follow in the footsteps of the `discoverMovies` function. But a few things must be different:
* You will send the request to a slightly different url (we want to talk to a different "endpoint" on the API)
* Your `data` object must include another property, `query`, whose value will be the search term the user typed in (e.g. "coconut")

### How to Submit

Just like last time, commit your work on Git and push to a new branch on your GitHub repo. Then, submit a link to your repo on Vocareum.

##### Commit and Push

If you run the `git status` command, you should see that you now have *unstaged* changes:

```nohighlight
$ git status
On branch studio2-my-work
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
On branch studio2-my-work
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
        modified:   css/styes.css
        modified:   index.html
        modified:   js/flicklist.js
```

All the files are now staged for committing. Go ahead and make a commit, using the -m flag to remind your future self (and others looking at your code) what changes you made during this commit:

```nohighlight
$ git commit -m "finish FlickList 2 studio"
[studio2-my-work 46db232] finish FlickList 2 studio
 2 files changed, 2 insertions(+), 2 deletions(-)
```

The convention is to write your commit messages using the present tense rather than past tense (e.g. "finish" rather than "finished").

If you check your status one more time, you should see this:

```nohighlight
$ git status
On branch studio2-my-work
nothing to commit, working directory clean
```

Finally, *push* your changes to your remote repo:

```nohighlight
$ git push origin studio2-my-work
Counting objects: 62, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (20/20), done.
Writing objects: 100% (22/22), 2.36 KiB | 0 bytes/s, done.
Total 22 (delta 6), reused 0 (delta 0)
To https://github.com/jharvard/flicklist.git
 * [new branch]      studio2-my-work -> studio2-my-work
```

If you go back and revisit github.com/jharvard/flicklist, you should now see your new branch up there! Specificially, near the top-left of the screen, you should see a dropdown menu that says "Branch: master". Click that dropdown and you should see an option for "studio2-my-work". Click on that branch, and you should now see the code you just worked on. Copy the current url in your browser's address bar (you are about to paste that url into Vocareum).

##### Submit on Vocareum

On Vocareum, click the assignment titled **Studio: FlickList 2**. In your `/work` directory you should see a file called `studio2.txt`. Open up this file and fill in the link to your work on GitHub.
