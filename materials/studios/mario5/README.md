# Studio: Mario 5

Today you won't be adding any new features to the project. Instead you will refactor the existing codebase to use jQuery instead of "vanilla" Javascript for manipulating the DOM.

## Obtaining the Starter Code

1. Navigate into your `mario-js` directory.

2. Make sure you do not have any uncommitted changes:

    ```nohighlight
    $ git status
    On branch mario4
    Your branch is ahead of 'origin/mario4' by 1 commit.
      (use "git push" to publish your local commits)
    nothing to commit, working directory clean
    ```
    It should say "working directory clean".

    If you *do* have uncommitted changes, then `add` and `commit` them now.

3. Switch to the `mario5` branch:

    ```nohighlight
    $ git checkout mario5
    Switched to branch 'mario5'
    Your branch is up-to-date with 'origin/mario5'.
    ```

4. Pull down the latest changes.

    ```nohighlight
    $ git pull
    Already up-to-date.
    ```

    Sometimes, the staff might make last-minute changes to the starter-code. Running `git pull` here ensures that you will have the **very latest** version of the `mario3` branch.

    Usually you will just see:

    ```nohighlight
    Already up-to-date.
    ```

    But in the event that we **did** make some changes after your initial `git clone` on the first day of class, running `git pull` now pulls down those changes, and you will see a different message outlining the changes.


## Take a Look

#### Preview

If you open up the page in a browser, you will see that it looks the same as last time, but it doesn't function anymore. You can type in the textbox, but nothing happens when you submit the form. That's because we have started the refactoring process, and left some gaps for you to fill in.

#### Code Changes

Let's look over the code. Notice the following changes:

- At the bottom of `mario.html`, we have an additional `<script>` tag right before the one that loads `mario.js`. This script imports the jQuery library so that we can use jQuery's methods in our own code.

- We have refactored a few lines of code to use jQuery syntax:

	- registering the form's submission event handler:

		```js
		$("#draw-form").submit( function(event) { // lots of code ... } );
		```

	- The `clearError` function is implemented using jQuery.

	- At the bottom of `drawPyramid`, we use jQuery to create a `<p>` element whose inner HTML is equal to the string for the current row.


## Your Task

First, note that we provide a few helpful links in the [Tips](./#tips) section below.

Now go ahead and complete the following tasks:

1. At the end of the loop in `drawPyramid`, we have created a `<p>` element with the string content. But there is no longer any code to insert the element onto the page. Use jQuery to append the element as a child of the `<div id="pyramid">`.

2. Now you should be seeing a new pyramid added to the screen whenever you submit the form. Next, reimplement the "clearing away" of the previous pyramid so that they don't accumulate. At the beginning of `drawPyramid`, add some jQuery code to remove all the content inside the `#pyramid` container div.

3. Currently the pyramids always have a height of 5, no matter what the user types. Let's fix that. Inside the `submit` handler callback, replace the hard-coded `"5"` with some jQuery code to extract the actual value from the `<input>`.

4. The last thing to bring back is the error messages. When the user types something "bad", we currently don't provide any useful feedback. Fill in the implementation of `displayError` so that the user once again is able to see what she did wrong. You can use our implementation of `clearError` as a loose reference.

## Tips

- This [jQuery vs Vanilla JS Cheatsheet][cheatsheet] is useful (doesn't cover everything though).

- You will probably need to use at least the following jQuery functions:

    - [.val()][val]
    - [.append()][append]
    - [.text()][text]
    - [.addClass()][addClass]
    - [.empty()][empty]


## Committing Your Changes

1. Add your new changes:

    ```nohighlight
    $ git add mario.js
    ```

2. Then commit, along with a descriptive message.

    ```nohighlight
    $ git commit -m "refactor to use jQuery"
    ```


[cheatsheet]: https://gist.github.com/liamcurry/2597326
[append]: https://api.jquery.com/append/
[val]: https://api.jquery.com/val/
[addClass]: https://api.jquery.com/addClass
[empty]: https://api.jquery.com/empty/
[text]: https://api.jquery.com/text/
