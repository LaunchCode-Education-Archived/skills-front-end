# Studio: Mario 4

Last time, we added to our page an input field and a button so that the user could specify exactly how tall of a pyramid she wants drawn. You might have noticed, however, that the text box provides plenty of opportunities for the user to type things that don't make sense:

- words instead of numbers
- negative numbers
- nothing at all
- etc.

Today we will address these issues by adding some validation logic to make sure the user's input is sensible before drawing the pyramid, and to provide helpful error messages when the input is not sensible.

In this particular project, the whole "client-side validation" point is somewhat moot because there *is no* server-side code and everything happens on the front-end. But imagine if we added some back-end functionality which required sending the user's pyramid height over to a server. In that situation, we certainly wouldn't want to make the user wait a while before telling her she did something wrong and needs to try again.

## Obtaining the Starter Code

1. Navigate into your `mario-js` directory.

2. Make sure you do not have any uncommitted changes:

    ```nohighlight
    $ git status
    On branch mario3
    Your branch is ahead of 'origin/mario3' by 1 commit.
      (use "git push" to publish your local commits)
    nothing to commit, working directory clean
    ```
    It should say "working directory clean".

    If you *do* have uncommitted changes, then `add` and `commit` them now.

3. Switch to the `mario4` branch:

    ```nohighlight
    $ git checkout mario4
    Switched to branch 'mario4'
    Your branch is up-to-date with 'origin/mario4'.
    ```

4. Pull down the latest changes:

    ```nohighlight
    $ git pull
    Already up-to-date.
    ```

    Sometimes, the staff might make last-minute changes to the starter-code. Running `git pull` here ensures that you will have the **very latest** version of the `mario4` branch.

    Usually you will just see:

    ```nohighlight
    Already up-to-date.
    ```

    But in the event that we **did** make some changes after your initial `git clone` on the first day of class, running `git pull` now pulls down those changes, and you will see a different message outlining the changes.


## Take a Look

#### Preview

Preview `mario.html` in your browser. The page looks the same as last time, but you will notice that we have already started doing some validation.

Try typing and submitting each of the following inputs:

- "12"
- "Luigi"
- "-3"
- (nothing)
- "500"
- "8"

As you can see, some of these cases were handled very appropriately, but there are still some gaps left for you to fill in.

#### Code Changes

Now let's briefly look over the code. Notice the following changes:

- In `mario.html`, there are a few new CSS styles defined in the `<style>` tag. These cause the error message to have red text, and the input field to have a red border.
- In `mario.html`, we are using a `<form>` with an `<input type="submit"/>` instead of a `<button>`.
- In `mario.js`, we are handling the form's `onsubmit` event using an "anonymous" function defined right in the middle of the statement, rather than last time, when we used a named function (named `determineHeightAndThenDrawPyramid`).
- That anonymous handler function is much longer now than last time, largely because we have started to introduce validation logic.
- There are a few `TODO`s in there.
- There are two new functions, `displayError` and `clearError`. These functions simply toggle on and off, respectively, the visibility of an error message on the page. The `displayError` function is finished, but `clearError` contains a `TODO` for you.

## Your Task

1. Currently, if the user types nothing at all, they will receive an error message of *"That's not a valid height."* That kind of makes sense, but we can do better. In this scenario, it probably makes more sense to say something *"Please provide a height."*.

    Add an additional condition inside the anonymous `onsubmit` function, to check for the specific case where the user typed nothing at all. If the condition is true, give the user a more appropriate error message.

2. Currently, the user will receive the *"That's not a valid height."* error if she types something that cannot be parsed and wrangled into an integer. But **any integer** is allowed. Let's restrict that a little further so that negative numbers, and zero as well, for that matter, are considered invalid heights.

    Expand the conditional statement surrounding the *"That's not a valid height."* message so that only positive non-zero heights are allowed.

3. Notice that if the user triggers an error, and then corrects her error and re-submits the form (for example: types "foo" and submits and then types "12" and re-submits), the pyramid will draw correctly, but the old error message will not have gone away.

    Notice that at the beginning of the same `onsubmit` handler function, there is in fact a call to a function called `clearError`. So that sounds like it should do exactly what we need to do! The only problem is that the body of that function is empty aside from a `TODO` comment.

    Implement the `clearError` function so that it makes any currently visible errors disappear from the screen. This involves two things:

        1. Remove any text from that red label.
        2. Make sure the input element **does not** have a class of `invalid-field`.

    For reference, you can look at the `displayError` function. You want to do essentially the opposite of what that function does.

## Committing Your Changes

1. Add your new changes:

    ```nohighlight
    $ git add mario.js
    ```

2. Then commit, along with a descriptive message.

    ```nohighlight
    $ git commit -m "finish validating form submission"
    ```
