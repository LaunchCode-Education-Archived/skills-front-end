# Studio: Mario 2

In Mario 1, you implemented a function to print a "pyramid" to the developer console. Today, you will put that pyramid where it truly belongs: on your web page! To render the pyramid to the page, you will use Javascript to programatically insert it into the DOM.

## Obtaining the Starter Code

1. Navigate into your `mario-js` directory.

2. Make sure you do not have any uncommitted changes:

    ```nohighlight
    $ git status
    On branch mario1
    Your branch is ahead of 'origin/mario1' by 1 commit.
      (use "git push" to publish your local commits)
    nothing to commit, working directory clean
    ```
    It should say "working directory clean".

    If you *do* have uncommitted changes, then `add` and `commit` them now.

    Also note once again that you can ignore this part:

    > Your branch is ahead of 'origin/mario1' by 1 commit.
        (use "git push" to publish your local commits)

    because for Studios you do not care about staying in sync with the remote repository.

3. Switch to the `mario2` branch:

    ```nohighlight
    $ git checkout mario2
    Switched to branch 'mario2'
    Your branch is up-to-date with 'origin/mario2'.
    ```

    This switches your project to a "branched off" version of the project named `mario2`, where we have placed all the starter code for today's studio.

    If you look at your files now, you will see that they have changed. Cool! We will continue to use this branching system to give you starter code on future studios.

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

View the `mario.html` page in a browser window, you will see that the text on the page has changed since last time. It now says:

> Behold this wonderful pyramid!

The user is no longer instructed to open the Dev Tools console, because the pyramid is supposed to show up directly on the page. But, of course, instead of a pyramid, we see the same notice as last time:

> Uh oh! the pyramid is still under construction.

Now, if you do happen to open up the Console, you *will* see a pyramid show up down there. And that's because `mario.js` does include the solution to the previous studio.

Open up `mario.js` and take a look. You will see a fully implemented function that prints a pyramid to the console. The only difference is that the name of the function has changed from `printPyramid` to `drawPyramid`, and the "drawing" part is still unfinished. That's your job!

*Note* also that instead of spaces (`" "`), we are using periods (`"."`). We'll talk about that more further down. For now, just think of them as grains swirling in the desert wind.

Before getting started, quickly look at `mario.html`. Observe that inside the `<body>` is a `<div>` whose `id` attribute is equal to `"pyramid"`. We have placed this element here as a "container" which is sitting there waiting to be "injected" with the actual contents of the pyramid.

## Your Task

1. Complete the `TODO` at the bottom of the loop inside `drawPyramid`, so that each row gets inserted into to the DOM as a child element of the container `<div id="pyramid">`.

    In the scope of this loop, we have provided you with a variable called `rowStr`, containing a string for the current row (you can see it being printed with `console.log(rowStr)`). So you already have the string. You just need to add that string to the DOM.

    Create a `<p>` element and set its text to be the string, and then insert that paragraph element as a child of the the container `<div>` on `mario.html`.

2. Once you have the pyramid showing up, delete the "Under Construction" notice from the container `<div>`. Of course, the normal thing to do would be to delete those lines directly from your `mario.html` page. But just to get some more practice, `**don't do that**`. Instead, add another line to your `drawPyramid` function so that it programatically deletes the `<div id="notice">`.

*Note:* What's up with the periods instead of spaces? Well, just try switching back now and see what happens. As you have seen before, HTML tends to compress whitespace. This is often very convenient, but in this particular case, it messes up the alignment of our pyramid. A more reasonable thing to do, rather than use a period character, would be to use an HTML-encoded space character. We will use this technique in the next studio.

## Committing Your Changes

1. Add your new changes:

    ```nohighlight
    $ git add mario.js
    ```

2. Then commit, along with a descriptive message.

    ```nohighlight
    $ git commit -m "render pyramid to the DOM instead of the console"
    ```

    *Note* that in the commit message above, we use the *present tense* rather than the past tense (e.g. "rendered"). This might feel weird but is technically the preferred way of doing commit messages in Git.
