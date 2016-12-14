# Studio: Mario 3

Thus far, we have had this cool generic function which is able to draw a pyramid of *any* height, but we haven't taken full advantage of it. We simply hardcode a value of `5` as the argument passed in. Today you will extend the page to allow the user to specify whatever height they want.

## Obtaining the Starter Code

1. Navigate into your `mario-js` directory.

2. Make sure you do not have any uncommitted changes:

    ```nohighlight
    $ git status
    On branch mario2
    Your branch is ahead of 'origin/mario2' by 1 commit.
      (use "git push" to publish your local commits)
    nothing to commit, working directory clean
    ```
    It should say "working directory clean".

    If you *do* have uncommitted changes, then `add` and `commit` them now.

3. Switch to the `mario3` branch.

    ```nohighlight
    $ git checkout mario3
    Switched to branch 'mario3'
    Your branch is up-to-date with 'origin/mario3'.
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

Preview your `mario.html` file in a browser window. You will see that the page has changed a little bit:

- There is more text on the page.
- There a a few styles.
- Most importantly, there is an input field and a button, via which the user is invited to specify precisely how tall she wants the pyramid to be.

In `mario.js`, we have defined, and begun to implement, a function with the verbose name `determineHeightAndThenDrawPyramid`, which, once you have finished the implementation, will do exactly what its name implies: it will search the DOM in order to determine the height value that the user typed into the text box, and then it will cause a correctly-sized pyramid to show up on the page.

Below that, the `drawPyramid` function has not changed much since last time. There is one `TODO` in there for you. More on that later.


## Your Task

1. In `mario.js` attach a handler function to click events on this button from the html page: `<button>Draw a pyramid</button>`.

    You will first need to find a reference to that button. There are a variety of ways to do this. Feel free to edit the `mario.html` file and add an attribute to the button to help you grab a reference to it.

    Once you have a reference to the button, you must register a function to handle its click events. This function, when invoked, should determine the height that the user typed in to the text box, and then draw a pyramid with the correct height on screen. **Hint:** Maybe this function already exists...

2. Next, inside the `determineHeightAndThenDrawPyramid` function, you must figure out what height the user typed.

3. Now that you know the height, time to draw the pyramid. Once again, you already have a function that does exactly that, right? So don't over-think (or over-type) this step.

4. Almost done! But notice that each button-click results in a new pyramid being draw on screen, resulting in an ever-accumulating junkyard of pyramids. Add a line of code at the beginning of the `drawPyramid` function so that, before drawing anything, you first clear away the old content.

## Committing Your Changes

1. Add your new changes:

    ```nohighlight
    $ git add mario.js
    ```

2. Then commit, along with a descriptive message.

    ```nohighlight
    $ git commit -m "allow user to input pyramid height and respond to button click"
    ```
