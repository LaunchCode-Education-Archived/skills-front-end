##### Web Track
[Back to Class 3](../../class3)

# Studio: FlickList 3

Today you will add a little bit more functionality to the project, but the main improvements will be aesthetic. You will Bootstrapify the page, using the Bootstrap library to apply a bunch of nice styles, as well as a responsive Bootstrap Grid layout.

### Demo

Here is a demo of what you are trying to accomplish: <a href="http://htmlpreview.github.io/?https://github.com/LaunchCodeEducation/flicklist/blob/b19ea10df9355f8079047e8b1f48e0a8e31a2ba9/index.html" target="_blank">FlickList 3 Demo</a>. Play around with the demo for a minute and get familiar with its features. Also, keep the demo open in a separate window, so you can refer to it while working on the assignment.

Note the following additions since last time:
* Watchlist items have an "I watched it" button, which allows the user to cross that movie off their list.
* Watchlist items have pictures!
* The page layout changes responsively with the size of the screen. When the widnow is sufficiently wide, the browse list shows up in its own column, to the right of of the Watchlist. Otherwise, the browse list is positioned below the Watchlist as before. (Try this now if you haven't already. Open the demo and play modify the window size, and observe how the page layout responds.)
* Various stylistic changes

### Starter Code

First, fetch the studio3 branch from upstream:

```nohighlight
$ git fetch upstream studio3
remote: Counting objects: 21, done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 21 (delta 6), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (21/21), done.
From https://github.com/LaunchCodeEducation/flicklist
 * branch            studio2    -> FETCH_HEAD
   74b1223..fe10c4f  studio2    -> upstream/studio3
```

Then, checkout a new local branch:

```nohighlight
$ git checkout -b studio3-my-work upstream/studio3
Branch studio3-my-work set up to track remote branch studio3 from upstream.
Switched to a new branch 'studio3-my-work'
```

### A Brief Tour

Let's look briefly at what has changed in each of our files:

##### index.html

In `index.html`, the only important change is that we have wrapped our two `<section>`s together inside a `<div>` tag with a class of "main-content". We have also removed the "big-header" id from the `<header>` at the top of our page. Since we'll be using Bootstrap to style this header, we no longer need to give it an id. 

##### flicklist.js

The only change in `flicklist.js` is that the `api` object at the top of the file now has an extra property:

```js
var api = {
  root: "https://api.themoviedb.org/3",
  token: "TODO", // TODO 0 add your api key

  /**
   * Given a movie object, returns the url to its poster image
   */
  posterUrl: function(movie) {
    // TODO 4b
    // implement this function

    return "http://images5.fanpop.com/image/photos/25100000/movie-poster-rapunzel-and-eugene-25184488-300-450.jpg" 
  }
}
```

The object now has three properties: `api.root`, `api.token`, and `api.posterUrl`. But `posterUrl` is a tad special, because rather than a simple primitive type like a string or int, `api.posterUrl` is a function!

You can call this function like you would call any other:

```js
var myMovie = {}; // pretend we have some movie object lying around
var url = api.posterUrl(myMovie);
console.log(url); // => logs http://images5.fanpop.com/image/photos/25100000/movie-poster-rapunzel-and-eugene-25184488-300-450.jpg
```

One of your tasks will be to implement this function so that it returns, for a given movie, the url to a jpg somewhere on the internet where that movie's poster image lives.

##### styles.css

We've made a few small changes here, like making the backgorund color of the browse section black, and adjusting a jew margin and padding values. 

Notice that in some cases we use a new unit of measurement, the percent, for specifying values. For example, all sections now have a `padding: 2%;" rule. Using 2% rather than a rigid pixel value means that the exact padding changes depending on the width of the container of the section. This helps make our page more responsive, because a certain number of pixels, like say 20px, might seem too small when the screen is very large, but might be too much once the screen is very small.

Finally, notice that we specify `<hr>` elements to have a border color of `rgba(128,128,128,0.2)`. This gives the `<hr>` a translucent gray color.

### Assignment

The source code has a bunch of TODOs. There are more total tasks than in previous studios, but many of them are very small. 

Work your way, in order, through the following tasks:

#### 0. API key

As usual, add your api key to the object near the top of `flicklist.js`.

#### 1. An "I watched it" Button

In flicklist.js, inside the `render` function, add a button to each Watchlist item. When clicked, the appropriate movie should be removed from `model.watchlistItems`, and `render` should be called again.

To remove the item from the array, you can use a new array function called <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice">splice</a>. You'll also need to use `indexOf` again (you should be familiar with this function from the previous studio), in order to determine where to splice from the array.

#### 2. Bootstrap Makeover Party

Bootstrap comes with a ton of nice pre-made CSS styles "right out of the box". We simply need to give our elements the appropriate class names, and they will automagically change appearence. There are a bunch of places all around the project where you will do this.

##### 2a. Include the Library

The first step is to simply include the Bootstrap library in our project, at the top of `index.html`. 

On their website, Bootstrap even <a href="http://getbootstrap.com/getting-started/" target="_blank">provides us</a> the exact `<link>` tag we need to copy/paste into our project in order to grab the library from their CDN:

```html
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">
```

##### 2b. Style the Page Header

The first Bootstrap class we'll use is <a href="http://www.w3schools.com/bootstrap/bootstrap_jumbotron_header.asp" target="_blank">Jumbotron</a>, which is used for creating a big, bold, attention-grabbing block of text. Use it to style the `<header>` at the top of the page. 

Next, add the "text-muted" class to the subtitle, so it stands out a little less.

##### 2c. Customize the Jumbotron

In addition to just using Bootstrap classes as they are, we can also customize them to fit our needs. Doing so is as simple as adding our own CSS selector for `.jumbotron`, and specifying whatever styles we want to overwrite. 

Do that now, in `styles.css`. Make the jumbotron class have centered text (rather than left-aligned). 

Also, the jumbotron by default has a margin of 30 pixels. This is going to become a little much if the user is on a smaller screen. Change the bottom margin to a value of `1%`. This both reduces the margin, and makes it "fluid", calculating it as a percentage of the width, rather than a fixed value.

Finally, note that this customization only works because in the head of `index.html`, we include our own stylesheet AFTER including Bootstrap. 

##### 2d. Style the Browse List

This task involves changing code in both `index.html` and `flicklist.js`.

Read more about <a href="http://v4-alpha.getbootstrap.com/components/list-group/" target="_blank">Bootstrap Lists</a> and <a href="http://v4-alpha.getbootstrap.com/components/buttons/" target="_blank">Bootstrap Buttons</a> for guidance.

##### 2e. Style the Form

For guidance, read more about <a href="http://v4-alpha.getbootstrap.com/components/input-group/" target="_blank">Boostrap Input Groups</a>, especially <a href="http://v4-alpha.getbootstrap.com/components/input-group/#button-addons" target="_blank">Button Addons</a>.

##### 2f. Style the Watchlist

This one's very simple. In index.html, just give the watchlist `<ul>` a class of <a href="http://getbootstrap.com/css/#inline" target="_blank">list-inline</a>. Remember that whole `"inline-block"` shenanigans we did last time? This class was made specifically for lists like the kind we're doing here.

##### 2g. Style the Watchlist Items

In `flicklist.js`, restyle the watchlist items using <a href="http://getbootstrap.com/components/#panels-heading" target="_blank">Bootstrap Panels</a>.

##### 2h. Customize the Watchlist Items

Let's customize these things a little more. Each `<li>` should have:
* no padding at all
* a little bit of margin on the right and bottom edges
* a width of exactly 160 pixels

##### 2i. Style the "I watched it" Buttons

Make 'em red. Here is the section on <a href="http://v4-alpha.getbootstrap.com/components/buttons/" target="_blank">Bootstrap Buttons</a> again.

##### 2j. Customize the "I watched it" Buttons

In `flicklist.js`, add some additional styles to these buttons. We want the button to fill the entire width of its container, and sit 10px below its upper neighbor.

#### 3. Responsive Grid Layout

Now let's implement the grid layout. When the page is sufficiently wide, we want the browselist to show up to the right of the Watchlist, rather than below it. 

##### 3a. Implement the Grid

In `index.html`, add another `<div>` inside the main content div, but still wrapped around both sections. This new div should have a class of "row". 

Next, give each section a class of "col-?-?" (the question marks are for oyu to figure out). You want the watchlist to take up 5/12 of the width of the screen, and the browselist to take up the remaining 7/12. The "breakpoint" should be tablet devices-- in other words, if the user is on an iPad or anything smaller, then the column layout switches back to normal, with the browselist on its own block below the watchlist.

Resize your window and see if it's working properly. At a certain point, the layout should switch back and forth.

Read more on <a>Bootstrap Grids</a> for guidance.

##### 3b. Add a Meta Viewport Tag

Open up the developer tools and click the little icon of a tablet and a phone. This will allow you to simiulate varous devices in the browser.

Uh-oh! Things don't look so great for these devices. Why not? Our layout is responsive...

It turns out there is one more little tag we need to add to the top of our html file:

##### 3c. Center items in the Watchlist

Notice how on some really skinny screens, like the iPhone5, there is only enough horizontal space to fit one Watchlist item per block. It looks especially silly because the items are all floating to the left, so there is a lot of space to their right. We can fix this by simply applying a `text-align: center` style to the `<ul>` container. 

Now the items center themselves!

```html
<meta name=viewport content="width=device-width, initial-scale=1">
```
From now on, this is another one of those tags that you probably want to include in all your HMTL right from the beginning. This sets the width of the page's viewport to be equal to the width of the user's device. Read more <a href="https://developers.google.com/speed/docs/insights/ConfigureViewport#additional-information">here</a>.

#### 4. Poster Images

The last task to tackle is to add poster images to the Watchlist items. This involves two parts:

##### 4a. Add Image Element to Watchlist Item

Inside `render`, use jQuery to make an `<img>` element, and set its `src` attribute equal to the result calling of the `posterUrl` function inside the `api` object at the top of the file. When calling the function, don't forget to pass your movie in as an argument. 

Once you have the element, append it inside the "body" portion of the Bootstrap panel (rather than the "heading" portion).

Also, give the image element a class of "img-responsive". This is another Bootstrap class that does some work for us, for example setting the element's width to be 100% of its container (and not more! otherwise it will stick out past the bounds of the container).

##### 4b. Implement the posterUrl function

Now we have to actually implement that function. Currently it just returns a hard-coded url. We want to examine the movie that was passed in, and figure out what the actual url should be. 

To help you figure that out, here are three example urls to real movie posters:
* http://image.tmdb.org/t/p/w300//jjBgi2r5cRt36xF6iNUEhzscEcb.jpg
* http://image.tmdb.org/t/p/w300//kqjL17yufvn9OVLyXYpvtyrFfak.jpg
* http://image.tmdb.org/t/p/w300//nBNZadXqJSdt05SHLqgT0HuC5Gm.jpg

Use a console.log statement to print a movie object and poke around and see if you can find anything that might help construct the full url for a particular movie.

#### 5. Remove Dead Code

There's a chunk of CSS code we no longer need after switching to Bootstrap. For example, Bootstrap automatically applies some transparency to disabled buttons. 

All the rest of the CSS at the bottom of the file is obsolete. Go ahead and delete it!

### How to Submit

As usual, first, commit your work on Git and push to a new branch on your GitHub repo. Then, submit a link to your repo on Vocareum.

##### Commit and Push

If you run the `git status` command, you should see that you now have *unstaged* changes:

```nohighlight
$ git status
On branch studio3-my-work
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
On branch studio3-my-work
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
        modified:   css/styes.css
        modified:   index.html
        modified:   js/flicklist.js
```

All the files are now staged for committing. Go ahead and make a commit, using the -m flag to remind your future self (and others looking at your code) what changes you made during this commit:

```nohighlight
$ git commit -m "finish FlickList 3 studio"
[studio2-my-work 46db232] finish FlickList 3 studio
 3 files changed, 3 insertions(+), 3 deletions(-)
```

The convention is to write your commit messages using the present tense rather than past tense (e.g. "finish" rather than "finished").

If you check your status one more time, you should see this:

```nohighlight
$ git status
On branch studio3-my-work
nothing to commit, working directory clean
```

Finally, *push* your changes to your remote repo:

```nohighlight
$ git push origin studio3-my-work
Counting objects: 62, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (20/20), done.
Writing objects: 100% (22/22), 2.36 KiB | 0 bytes/s, done.
Total 22 (delta 6), reused 0 (delta 0)
To https://github.com/jharvard/flicklist.git
 * [new branch]      studio3-my-work -> studio3-my-work
```

If you go back and revisit github.com/jharvard/flicklist, you should now see your new branch up there! Specificially, near the top-left of the screen, you should see a dropdown menu that says "Branch: master". Click that dropdown and you should see an option for "studio3-my-work". Click on that branch, and you should now see the code you just worked on. Copy the current url in your browser's address bar (you are about to paste that url into Vocareum).

##### Submit on Vocareum

On Vocareum, click the assignment titled **Studio: FlickList 3**. In your `/work` directory you should see a file called `studio3.txt`. Open up this file and fill in the link to your work on GitHub.
