##### Web Track
[Back to class 1](../../class1)

# Studio: FlickList 1

In [the previous Studio](../flicklist-0), you forked the project repository and added your API key to the source code.

Today, you will start adding some real functionality to the code base. By the end of this studio, users will see a browseable list of movies on the screen. Each movie will have a "Add to Watchlist" button, which, when clicked, will cause that movie to show up on another area of the screen where the user's Watchlist is displayed.

### Demo

Here is what you are trying to accomplish: <a href="http://htmlpreview.github.io/?https://github.com/LaunchCodeEducation/flicklist/blob/ba335b0509258c7e4dc51779f9baa536f914c07b/index.html" target="_blank">FlickList 1 Demo</a>. Take a minute to play around with the demo so you understand what your goal is.

### Git Yer Hands on Some Starter Code

Navigate to the proper directory:

```nohighlight
$ cd ~/workspace/web-track/studios/flicklist
```

Your git status should be clean of any unstaged changes:

```nohighlight
$ git status
On branch studio0-my-work
nothing to commit, working directory clean
```

(We are assuming you will still be on the `studio0-my-work` branch from last time. But if you're on a different branch, that's fine, as long as you see "nothing to commit, working directory clean". If you do have unstaged or uncommitted changes, commit them now. If you need guidance, see [here](../flicklist-0#how-to-submit).)

Now let's fetch the `studio1` branch from the upstream repo:

```nohighlight
$ git fetch upstream studio1
From https://github.com/LaunchCodeEducation/flicklist
 * branch            studio1    -> FETCH_HEAD
```

and then checkout a new local branch with the contents of upstream/studio1

```nohighlight
$ git checkout -b studio1-my-work upstream/studio1
Branch studio1-my-work set up to track remote branch studio1 from upstream.
Switched to a new branch 'studio1-my-work'
```

(Just an aside: The `-b` flag allows you to create and switch to a branch in one line. It's just a fancier version of this:
```nohighlight
$ git branch studio1-my-work upstream/studio1
Branch studio1-my-work set up to track remote branch studio1 from upstream.
$ git checkout studio1-my-work
Switched to a new branch 'studio1-my-work'
```
You can use whichever you feel more comfortable with.)

### A Brief Tour

Welcome to the studio1 branch!

Your folder structure should look the same as last time:

```nohighlight
$ tree
.
├── index.html
└── js
    └── flicklist.js

1 directory, 2 files
```

But the contents of those files is a little different. Let's take a look. Open up `index.html` and `flicklist.js` in your IDE.

##### index.html

The body of the document now has three main parts:
* a `<header>` to display the project title and tagline
* a `<section>` to display the movies that are on the user's watchlist
* a TODO, where you will implement another `<section>`, this one to display a browsable list of popular movies

The `<header>` and `<section>` tags might look unfamiliar to you. They are relatively new additions to the HTML language. Similar to the `<div>`, these tags serve as a container for other tags, so you can group your document into chunks. The difference is that a `<div>` does not indicate *what kind of content* it contains, whereas these new tags do: the `<header>` indicates that it is meant to serve as a title or heading above some other content; the `<section>` indicates a discrete section of your document. Using these tags instead of `<div>`s makes it more immediately obvious how your document is structured and what kind of role each of the various chunks is playing. As much as possible, it is generally best practice to make your HTML "semantically meaningful" like this. You will learn a bit more about "Semantic HTML" in later Prep Work.

You might also notice that although the top of this file is almost the same as last time, there is one small change-- we've added is this line:

```html
<meta charset="utf-8"/>
```

What this does is explicitly defines that our document should use the Unicode character encoding. If curious, you can read more about character encoding <a href="http://www.w3.org/International/questions/qa-what-is-encoding" target="_blank">here</a>. Generally try to remember to add this line in your HTML, or you might get some strange results when your page attempts to display obscure characters. But for now, don't waste a ton of brainpower worrying about this topic.

##### flicklist.js

Let's now talk `flicklist.js`. 

The beginning of the file still contains that `api` object, one of whose properties, `token`, currently has a value of `"TODO"`, which you should once again replace with your personal api key.

There is another object nearby, called `model`. This is where we will store all the data we need to keep track of. You can see that this object has two properties:
* `watchlistItems`, an array (initially empty) that represents all the movies on the user's watchlist
* `browseItems`, an array (also initally empty) that holds all the movies we want to make available to the user for browsing.

Moving down the page, the `discoverMovies` function is very similar to the function called `testTheAPI` from last time: it makes an AJAX request to TheMovieDB's API, and after receiving a response, logs it to the console. But there is now a little bit more code inside that `success` function:
* First of all, there is a TODO! We want you to write a line here such that, whenever a response comes back from the API, you update the `model` variable so that its `.browseItems` property is equal to the list of movies in the response.
* After updating the model, we invoke a function called `callback`. Where did that function come from? It turns out it was passed into us as an argument to `discoverMovies`. A very powerful feature of JS is the ability to pass functions around as arguments to other functions. The idea of a <a href="https://en.wikipedia.org/wiki/Callback_(computer_programming)" target="_blank">callback</a> is that whoever is invoking `discoverMovies` can pass in a block of code to specify what should happen after the response comes back.

To see this in action, scroll down to the bottom of the file, and you'll see where `discoverMovies` is used. When the document is loaded, we execute this line:

```js
discoverMovies(render);
```

which invokes `discoverMovies` and passes in something called `render` as the callback. In other words, we are saying: Go fetch some results from the API, and when you get a response back, invoke this other function called `render`. 

Scroll up a bit, and you'll see that the `render` function is defined directly above. The purpose of this function is to re-display everything in the DOM based on the current information stored in the `model` variable. It is mostly empty so far, but contains a handful of TODOs. 

##### Debugger Walkthrough

To help wrap your head around all this, do the following exercise:

1. Preview the page in the Chrome browser
2. Open the developer tools
3. Click the "Sources Tab"
4. Locate `flicklist.js` and click on that. You should see the source code appear.
5. Expand the sub-window displaying the source code to be a little bigger, so you can actually see the code.
6. Add breakpoints to the following lines: 
  * line 21
  * line 27
  * line 45
  * line 69
7. Refresh the page.
8. You should hit your first breakpoint (line 69.) Click the continue button and you should hit another breakpoint. At each breakpoint, click the Step-Over button a few times to get a feel for what's happening, and then click Continue button and observe which section of code fires next.

### Assignment

Work your way through the TODOs in the starter code. Each task is numbered, indicating the order in which you should work on them. The tasks are as follows:

##### 0. Add your API key to the `api` variable

Just like last time.

##### 1. Add a browsing section

In `index.html`, add another `<section>` very similar to the watchlist section above. You should give your section an `id` so that you can refer to it later and manipulate its contents. You should also put an empty `<ul>` inside, where you will later insert those list items for the browsable movies.

##### 2. Update the model when AJAX request succeeds

Inside the `discoverMovies` function, when a successul response comes back, we are currently logging the response to the console, but we are not actually doing anythign useful with the data. Your job is to update the `model` variable, filling its `.browseItems` property with the newly received list of movies.

##### 3. Insert a list item for each movie on the browse list

The rest of your TODOs are inside the `render` function. For these, jQuery is your best friend. 

On this one, we are asking you to create a list item `<li>` for each movie in the browse list, and append that list item to the `<ul>` inside the browse section on the document. The list item for now should jsut contain the title of the movie.

You might be wondering: we had you assign an id to the section, but not the `<ul>` inside the section, so how can you obtain a reference to the `<ul>`? Just like CSS, jQuery allows you to traverse the DOM using <a>descendant selectors</a>, for example:

```js
$("#essay p")
```

yields all `<p>` tags who are descendents (children, or children's children...) of the element whose id is "essay". 

To complete this task, you will need to make use of jQuery's <a href="http://api.jquery.com/append/" target="_blank">append</a> and <a href="http://api.jquery.com/text/" target="_blank">text</a> functions. 

The following code demonstrates how to add a link to the bottom of every descendant paragraph inside the "essay" element:

```js
var googleLink = $("<a></a>").text("Click me!").attr("href", "google.com");
$("#essay p").append(googleLink);
```

Ultimately, you should be generating HTML that looks something like this:

```html
<ul>
  <li>
    <p>The Night Before Christmas</p>
  <li>
  <li>
    <p>The Morning After Christmas</p>
  </li>
  <li>
    <p>Eyes Wide Shut</p>
  </li>
  ...
</ul>
```

##### 4. Each browse list item should contain a button

Once you have list items displaying the titles of all the movies, the next step is to add a button to each item. The button should say "Add to watchlist".

This step should be pretty simple. Just append another item inside the list item, after the movie title.

##### 5. Add click handlers to the buttons

Once those buttons are showing up, your next task is to make them actually do something. Use jQuery's <a href="http://api.jquery.com/click/" target="_blank">click</a> function to register a "click handler" on each button. This is another one of those functions where you pass in a "callback", in order to specify exactly what should happen when the click event occurs. You'll want to pass in a function that accomplishes two things: appends to `model.browseItems` whichever movie was clicked, and then re-invokes `render`. Here is an example of a button whose click handler contains an "annonymous function" that accomplishes some tasks: 

```js
var myButton = $("<button></button>").text("Click if you dare");
myButton.click(function() {
  console.log("You clicked my button!");
  console.log("I love you!");
  releaseTheHounds();
});
```

Whenever `myButton` is clicked, the console will log "You clicked my button!", followed by "I love you!", and then some other function called `releaseTheHounds` will execute.

##### 6. Insert a list item for each movie on the Watchlist

Now that your buttons wired up and pushing new movies onto `model.watchlistItems`, the next step is to render those watchlist movies on the screen so the user can see them. 

Create a similar `forEach` loop to iterate over `model.watchlistItems` and append content to the `<ul>` inside the watchlist `<section>`.

Once you've finished, you should start to see movies appearing on the watchlist whenever you click the buttons! You will probably notice some weird behavior, where the same movie shows up multiple times after a few clicks. You might also notice that the browse list is grwoing longer and longer! You will tackle that next.

##### 7. Clear out the old list elements before re-rendering

You're seeing repeats of the same movies because each time `render` is executed, it re-renders *every* movie in the watchlist, not just the newly added movie. Similarly, the browse list is re-appending every single movie onto the DOM, even though they were already there.

To fix this, simply add some code at the beginning of the function which clears both lists. Use jQuery's <a href="http://api.jquery.com/empty/" target="_blank">empty</a> function, which deletes all the child nodes of an element. 

You may think this is an inefficient way having the browser render stuff, and in fact, you are right. After all, why should we delete all 20 items from the browse list, only to re-add them an instant later? Fortunately, the operations we are doing here are small enough that the inefficiency won't lead to a drop in performance significant enough to hurt the user experience. And the benefit of this monolithic `render` function is that we don't have to worry about which particular event we are responding to (Did a response come back from the API? Did the user just click a button? Which button?). All we have to worry about is, given the current state of the model, this is what our view should look like. The mental simplicity that this system affords us will grow more and more valuable as our program grows in complexity. 

### How to Submit

##### Commit and Push on Git

If you run the `git status` command, you should see that you now have *unstaged* changes:

```nohighlight
$ git status
On branch studio1-my-work
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   index.html
        modified:   js/flicklist.js

no changes added to commit (use "git add" and/or "git commit -a")
```

We can stage these changes with the `add` command:

```nohighlight
$ git add --all
```

The `--all` adds all (both of) the unstaged files, so you don't have to type them one by one.

If you check your status again now, you should see:

```nohighlight
$ git status
On branch studio1-my-work
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   index.html
        modified:   js/flicklist.js
```

Both files are now staged for committing. Go ahead and make a commit, using the -m flag to remind your future self (and others looking at your code) what changes you made during this commit:

```nohighlight
$ git commit -m "finish FlickList 1 studio"
[studio1-my-work 46db232] finish FlickList 1 studio
 2 files changed, 2 insertions(+), 2 deletions(-)
```

The convention is to write your commit messages using the present tense rather than past tense (e.g. "finish" rather than "finished").

If you check your status one more time, you should see this:

```nohighlight
$ git status
On branch studio1-my-work
nothing to commit, working directory clean
```

Finally, *push* your changes to your remote repo:

```nohighlight
$ git push origin studio1-my-work
Counting objects: 62, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (20/20), done.
Writing objects: 100% (22/22), 2.36 KiB | 0 bytes/s, done.
Total 22 (delta 6), reused 0 (delta 0)
To https://github.com/jharvard/flicklist.git
 * [new branch]      studio1-my-work -> studio1-my-work
```

If you go back and revisit github.com/jharvard/flicklist, you should now see your new branch up there! Specificially, near the top-left of the screen, you should see a dropdown menu that says "Branch: master". Click that dropdown and you should see an option for "studio1-my-work". Click on that branch, and you should now see the code you just worked on. Copy the current url in your browser's address bar (you are about to paste that url into Vocareum).

##### Submit on Vocareum

On Vocareum, click on the assignment called **Studio: FlickList 1**.

You should see a file called `studio1.txt`. In this file, provide us a link to the work you just pushed to GitHub. Then click "Submit".
