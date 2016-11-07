# Word Up!

As we near the end of a long Skill Track full boring things like movies, GIFs, and pyramids--the practicalities of life that, though perhaps necessary, are rather dull--you deserve some fun and games. So for this assignment, you will make a fun game!

----
## The Goal

The game you are trying to build is called *Word Up!*, and it is best described as a cross between Scrabble, Solitaire, and the Hunger Games in Space.

#### Demo

First things first: [Click here for a demo of what you are trying to accomplish][demo].

[demo]: http://htmlpreview.github.io/?https://github.com/jesseilev/word-up/blob/demo/index.html


Take note the following:

#### Rules of the Game

- The object of the game is to spell as many words as possible before time runs out, using only the letters specified.
- A word is invalid if it contains any letters that aren't in the specified set of allowed letters.
- A word is also invalid if it turns out not to be a real word.
- Your total score is the sum of the scores of all your valid words.
- The score of each word is the sum of the scores of each of its letters.
- The score of a letter is simply its score from the boardgame Scrabble.
- Unlike in Scrabble, you **may** use the same letter more than once in a single word.

#### The User Interface

- When the user clicks `New Game`, the letters are revealed and she can begin typing words.
- The letters are presented as little "chips" (I am going to refer to these things as chips throughout the assignment).
- Each letter chip contains a smaller chip indicating its points value.
- As the user types, the page provides continuous feedback. Specifically, if the word she is currently typing contains any letters that are not allowed, then the disallowed letters appear as red chips underneath the textbox.
- If the user tries to submit (presses Enter after typing) a word that contains disallowed letters, then the textbox simply clears and the word is not submitted.
- Once the user does submit a word containing only valid letters, it appears in a chip below the textbox.
- Shortly after a word chip appears, it will sprout a smaller (blue or red) chip indicating the points total for the word. A normal word will contain a blue chip with a number indicating its score. But a gibberish, nonexistent word will instead contain a red chip with an "X".
- Once the timer runs out, the textbox is no longer usable.
- Overall, everything looks freshhhh.

#### Room for Improvement

Note as well that there are some obvious places where the game could be improved, especially when it comes to the selection of the allowed letters:

- Sometimes none of your 7 letters are vowels, making it very hard to spell words!
- There is no special provision to make sure that if you receive a `q`, you also receive a `u`.
- Weird rare letters like `z` and `x` happen no less frequently than common letters like `e` and `t`.

Just wanted to point out that all these flaws are part of the assignment, and you are not required to fix them.

Of course, if you finish the normal assignment and want to improve the game, either by tweaking these imperfections or by adding cool new features, you are obviously encouraged to do so!

---
## The Pearson Dictionary API

Before diving into the code, let's take a second to get familiar with the API we'll be using.

What service do we need an API for? A dictionary. Our way of checking the validity of the user's word submissions will be to look up each word in the dictionary and see if it exists.

#### Pearson

[Pearson][pearson] is some mysterious organization that provides free tech services, or something... honestly IDK who they are. But their [Dictionary API][pearson-api] is dead-simple to use. You don't even need to register for a developer key.

[pearson]: http://developer.pearson.com
[pearson-api]: http://developer.pearson.com/apis/dictionaries

Let's use Pearson's dictionary to search for the word "cheese": Open up a terminal make a `curl` request to this url:

```nohighlight
$ curl "http://api.pearson.com/v2/dictionaries/entries?headword=cheese"
```

You should shortly receive a fat wall of JSON about cheese.

As you can see, the main endpoint we want to hit is `http://api.pearson.com/v2/dictionaries/entries`, and we pass along an additional `headword` parameter with a value of `cheese`.

#### Specifying a Particular Dictionary

There is one more complication, which is that their default dictonary is very permissive. For example, pretty much any combination of two or three letters you can imagine will probably turn up a few results as an acronym for something. This is bad, because we don't want our game to reward players who simply hack away at random short combinations of letters.

Luckily, the API allows you to choose a more specific dictionary by changing the endpoint url to:

`http://api.pearson.com/v2/dictionaries/DICTIONARY_CODE/entries`

where you substitute a particular dictionary name in for `DICTIONARY_CODE`. See the [API page][pearson-api] for more details.

I have gotten pretty good results using the "Longman Active Study Dictionary", whose code name is `lasde`.

Great, you should now have all the tools you need to start looking up words in the dictionary! This will come in handy towards the end of the assignment.

---
## Obtaining the Starter Code

[Clone this repository][word-up-repo].

[word-up-repo]: https://github.com/launchcodeeducation/word-up

---
## A Brief Tour of the Starter Code

Let's briefly look over the code you have inherited.

#### Preview in the Browser

Before looking at the code itself, you might want to quickly open up `index.html` in a browser window so you can see what the starter code *does*.

It's not much to look at, to be honest: just a header and a dilapidated scoreboard.

#### index.html

Now open up the source code in your text editor.

In `index.html`, note the following:

- We load some familiar assets, like jQuery and Bootstrap's CSS file.
- The body of the document has a `<main>` element which is divided into two sections:
	- The `"pregame"` section, which contains elements that will be shown before the game starts. This section contains a scoreboard, and will soon contain a "New Game" button once you finish your first task.
	- The `"game"` section, which is initially hidden, and will only be revealed once the user clicks the "New Game" button. This section contains the form where the user types, and some containers that will be dynamically injected with chips (one for the letters, one for the submitted words).
- We load our own `scripts/wordup.js` script.

#### scripts/wordup.js

Turn your attention now to the `wordup.js` file.

This is a very large file, but you will definitely find it worth your while to spend 5-10 minutes looking it over and reading all the comments. I wrote those comments myself, and I *will* be offended if you don't read them.

Broadly, the file is split up into a few sections:

- **Model Stuff**

	In this section we define a variable called `model` which holds all the information we need to keep track of. The model is like the current state of the app.

	This section also includes helper functions, such as `addNewWordSubmission`, which provide an interface for making changes to the model.

- **View Stuff**

	This section deals with manipulating the DOM to display everything on screen to show the user the current state of the model.

	The main function in this section is `render`. Render simply looks at the model, and re-draws everything it might need to draw, based on what the model looks like. Whenever the model changes, we will call `render` again to make sure the view is up to date. We used this same pattern in the FlickList project.

	This sections also contains a few helper functions to draw specialized parts of the view.

- **DOM Event Handlers**

	This section is pretty small. It just registers some callback functions as handlers for a few DOM events, such as when the user clicks the "New Game" button, or submits the form.

- **Game Logic**

	This section simply contains a bunch of helper functions relating specifically to the rules and logic of the game.

#### css/styles.css

Finally, take a look at `styles.css`. There are no TODOs on this file, but  in order to do some of your Javascript code, you are going to need to be familar with our scheme for applying CSS classes to the various elements of the page.

Specifically, it is important to understand how we style the various "chips" we are using. All of the different types of chips are some form of the Bootstrap [.tag][bootstrap-tag] class (<-- You should keep that link open in another window).

[bootstrap-tag]: http://v4-alpha.getbootstrap.com/components/tag/

The `.tag` class is just a little colored rectangle with rounded corners, intended for things like the little red number on Facebook that tells you how many new notifications you have. But one nice aspect of tags is that they have `display: inline-block`, which means if you put a bunch of them next to each other, they will wrap around to the next line, rather than disappear off the right-hand edge of the screen.

In our app, we use `tag` as well as some additional custom classes that we define:

- `tag-lg` for the larger tags that display the letter chips and word chips
- `tag-sm` for the "inner" tags that annotate each chip with its points value or some other information.

Note also that rather than the stable Bootstrap 3, we are using Bootstrap 4, which is still in "alpha" development (we are on the *bleeding edge!*), because we want to use those tags.

---
## Your Tasks

Time to get started!

I have bad news and good news for you. The bad news is that you have a lot (21!) of `TODO`s. The good news is that each task is relatively small, often only one or two lines of code, and you will be given somewhat detailed guidance.

<img src="http://66.media.tumblr.com/2e96a51d21f3fa17d94af64c8cea61bd/tumblr_ndwyr0McLD1thj99uo4_250.gif" />
<br>

Your tasks are as follows:

#### 1. New Game Button

Add a "New Game" button in `index.html`.

- If you give it the correct id, it will magically work.
- If you give it the correct CSS classes, it will magically look nice.

*Confirmation:*

 - Clicking should cause the textbox to appear.

#### 2. Time Remaining

In the `render` function in `wordup.js`, update the *Time Remaining* data on the scoreboard.

- For reference, we do something fairly similar in the line above, to set the current score.

*Confirmation:*

- You should see that the time appears on initial page load.
- Even better, you should also see that the time starts to count down when New Game button is clicked! The reason this works is that, each second, the `startTimer` function is updating the model and re-invoking `render`.
- You will also notice that every time the timer ticks, the user's text input is wiped clear from the textbox. That's not good! We will fix this soon.

#### 3. Focus the Textbox

Another thing that should happen, just to make the user experience a little better, is that the textbox should automatically receive "focus", so that the user can start typing immediately without having to physically click on it.

- In the `render` function, use the jQuery `.focus` method to give focus to the textbox.

*Confirmation:*

- As soon as the textbox appears, it should already have focus.

#### 4. Instructions for the User

In `index.html`, add some instructions above the textbox so the user knows what to do, e.g.:

> Spell as many words as you can, using only these letters:

*Confirmation:*

- You should see your instructions... duh.
- It will obviously look a little wierd, because "what letters?"

#### 5. Letters Container

In `index.html`, make an empty `<div>` container so we can "inject" the letter chips into it.

- If you give it the correct id, it will magically work.

*Confirmation:*

- Should magically fill up with letter chips now.
- Notice if you click New Game again, the letters change!

Now would probably be a good time to show your page to a friend and brag, "Check it out, I'm practically done with this assignment." If only you knew what's in store...

#### 6. Handle Input Event

The next handful of tasks will tackle that cool feature where we give immediate feedback as the user types. Specifically, we want to provide feedback to inform the user whenever the word she is typing contains any disallowed letters.

First, we need to be notified whenever any typing ocurs. In `wordup.js`, inside the `$(document).ready` callback, add another event handler, which will fire in response to the textbox's "input" event. An "input" event fires very liberally, basically whenever anything changes. (Recall that in the Pyramid Slide assignment, you listened for this same event on your slider component.)

- Use the jQuery `.on` method, with an event of `"input"`
- When the event fires, you should update `model.currentAttempt` to be equal to the current value of the textbox.
- Use the jQuery `.val` method.

*Confirmation:*

- You should now see that you have fixed the annoying bug in which user's text input was getting cleared away every second. Pop quiz: why was it happening, and why did this fix it?
- Additionally, if you open up the console and type `model.currentAttempt`, you should now see that it always matches the current text value that you have typed into the textbox.


#### 7. Implement the `isDisallowedLetter` function.

Now let's make some visible indication appear. Notice the block of code in `render` underneath where you focus the textbox. This code is attempting to check whether the user's current attempt contains disallowed letters, and if so, will restyle the textbox. The first line invokes a function called `disallowedLettersInWord`, which in turn makes use of another function called `isDisallowedLetter`, which is incomplete! Your job is to implement this function so that given any letter, it returns a boolean indicating whether or not the letter is "disallowed" by the current model.

- You can use the Javascript `indexOf` function as a way to check whether a particular thing is a member of a list.
- You might find it helpful to test the function in isolation by invoking it from the console, e.g. type `isDisallowedLetter("z")`, etc.

*Confirmation:*

- You should see that the textbox's text turns red whenever you type a disallowed letter.
- You might also notice that the text *stays* red, even after you delete the disallowed letter. We will fix that soon.


### 8. Red Letter Chips

We don't just want the text to turn red, we also want to inform the user about specifically *which* letters are not allowed. We do this by appending little red chips underneath the textbox, one for each disallowed letter.

In the `render` function, we have already written code that generates a list of those little red chips. You simply need to append those elements to the bottom of the `<form>`.

*Confirmation:*

- You should see the chips!
- You will also notice that they never go away, and very rapidly start to accumulate. We will address that soon.

### 9. Game Over

Changing gears now, when time runs out and the game is over, we don't want the user to be able to continue playing the current game. The textbox should become disabled when the game ends.

At the bottom of the `render` function you will see we have a block of code that checks whether the game is over, but the body of that conditional is empty with a TODO waiting for you.

- There is an HTML attribute called `"disabled"`, which you want to set to `true`.
- Another thing you should do is make sure to clear away any remaining text that was in the textbox. To clear its contents, just set its value equal to the empty string `""`.
- A neat trick you can use to test your code without having to wait 60 seconds for the timer to run out is to open up the console and manually change the model's `.secondsRemaining` property to something low, e.g. `model.secondsRemaining = 2;`.

*Confirmation:*

- The textbox should loose its focus and no longer be usable once the timer runs out.
- You might also notice that even upon starting a new game, the textbox remains disabled! That's not good. We will address that (and those other loose ends that have been building up) in the next task.

#### 10. Clear Stuff

All of the problems we have created in the previous three Tasks are similar. They are the result of us making a change, but never undoing that change. We can address them all in a very similar way: we simply need to reset everything to a "default" state at the beginning of our `render` function.

Notice the code block towards the top of `render` whose comment is `// clear stuff`. Your job is to add a few more pieces to this code block:

- The text in the textbox turns red, but it never changes back again. So use the jQuery `.removeClass` method on the textbox to remove the particular CSS class that is causing it to turn red.
- The red letter chips appear, but never disappear. So use the jQuery `.remove` method to remove all the red letter chips from the document. Remember that jQuery selectors can work with *groups* of elements. So to operate on all these chips at once, you need to use a selector based on a class that all the chips have in common, but no other elements share.
- The textbox remains disabled after the first game ends. So make sure you set its `"disabled"` attribute to `false`.

*Confirmation:*

- All the problems above should be fixed!

#### 11. Word Submission Chips

Back in the `render` function, append the wordSubmission chips to the DOM.

- You can do something very similar to what we did for the letter chips. You can get a list of chip elements by mapping a certain function over each submitted word.
- Then, you can append that list of HTML elements into the appropriate container.

*Confirmation:*

- You should now see the word show up whenever you submit the form.

#### 12. Implement the `containsOnlyAllowedLetters` Function

- This function is important because it is used by the `addNewWordSubmission` function as a way of filtering out illegal words. Once you finish this task, the user will no longer be able to submit a word that contains disallowed letters.
- You should make use of the `disallowedLettersInWord` function directly above this one.

*Confirmation:*

- If you type a word that contains disallowed letters and hit Enter, the form will simply clear away, but the new word will not be added.

#### 13. Pearson URL

In the `checkIfWordIsReal` function, provide the correct URL for the AJAX call for the particular word that was passed in.

*Confirmation:*

- When you submit a word, you should hopefully see this appear on the console:

	> We received a response from Pearson!


#### 14. Is it a Real Word?

Now that we got a response, we need to use that response to answer the question: Is this word legit?

In the same `success` callback of the AJAX call within the `checkIfWordIsReal` function, we have made a variable called `theAnswer`, and have assigned it a hardcoded value of `true`. Replace the hardcoded value with an actual answer.

Use the following (imperfect) hueristic to decide whether or not we have a "real word" on our hands: The `response` object contains a bunch of properties, one of which is a list of "matching entries" called `results`. If the `results` list is empty, then the word is not real. Otherwise, it is real.

*Confirmation:*

- Nothing visible. You should add your own `console.log` statement to check that this is working properly.

#### 15. Update `.isRealWord` of the Word Submission

Now that you know the correct answer, there is one more thing to do. You must find the appropriate item in `model.wordSubmissions`, and set its `.isRealWord` property accordingly.

<img src="https://media.giphy.com/media/3o7TKw7vcnyQa0Hldu/giphy.gif" style="width: 200px"/>
<br>

Let's back up a sec. (This will be a long digression, so get comfortable.)

You might have noticed, if you poked around on the console, that the `model.wordSubmissions` property is kind of weird. It turns out that the concept of a "word submission" is too complicated to be represented by a string alone. For each word, we need to keep track of two pieces of information: the string itself, and also whether or not the string is a real word (rather than just gibberish). So for each item in the `model.wordSubmissions` list, we actually want an *object* composed of two properties: a string, and a boolean.

For example, suppose the user is in the middle of a game, and has previously typed two words: `"honk"`, and `"honq"`. While "honk" is a real word, "honq" is not. And so in this situation, our model should look something like this:

```js
{
    ...
    gameHasStarted: true,
    secondsRemaining: 42,
    wordSubmissions: [
        { word: "honk", isRealWord: true },
        { word: "honq", isRealWord: false }
    ],
    ...
}
```

Makes sense so far?

<img src="http://66.media.tumblr.com/2e96a51d21f3fa17d94af64c8cea61bd/tumblr_ndwyr0McLD1thj99uo4_250.gif" />
<br>

Good, because it's about to get weirder.

The situation is further muddied by the fact that for each word submission, there is a brief period of time during which we *don't yet know* whether or not its string is a real word, because we are still waiting for a response from the dictionary API.

Suppose the user now submits another word, `"chunk"`. We need to add that to our `.wordSubmissions` list, but we do not immediately know whether or not "chunk" is a real word. You and I happen to know that "chunk" is real, but our program is dumb and must defer to the dictionary. So our program makes an AJAX call to the Pearson API. But remember that an AJAX call takes a few seconds to come back with a response, and in the meantime, we still don't have the answer. So during the brief period of time before the response comes back, we want our `model.wordSubmissions` to look like this:

```js
[
    { word: "honk", isRealWord: true },
    { word: "honq", isRealWord: false },
    { word: "chunk" }
]
```

Until we get the response back, the "chunk" object simply does not have a `.isRealWord` property.

As soon as we *do* determine the answer, we can update the model, so that the list becomes:

```js
[
    { word: "honk", isRealWord: true },
    { word: "honq", isRealWord: false },
    { word: "chunk", isRealWord: true }
]
```

That is how we want our program to behave. Each word submission object should contain a `.word` property, and *eventually* should also contain a `.isRealWord` property, after a brief delay. The first part is already done for you (go look at the `addNewWordSubmission` function again to see the code). But the second part is your job: you must add a `.isRealWord` property to the objects that don't already have them.

Let's finally turn to the task at hand. You are inside the `success` callback of the AJAX call to Pearson. You have just received the response for some particular word (let's continue pretending it is `"chunk"`), and you even you know the answer now (either `true` or `false`), assuming you did the previous TODO. Your current `model.wordSubmissions` is a list of objects, most of which contain two properties, but at least one (the one we care about, whose `.word` property is `"chunk"`) does not yet contain a `.isRealWord` property. Your job is to find that list entry, and set its `.isRealWord` property to the correct answer (in this case, `true`).

In coding terms, you simply need to iterate over the list of submissions, and for each submission, check if its `.word` property is equal to the string in question. If so, assign the correct value to its `.isRealWord` property.

*Confirmation:*

- As the user, submit a few words (some real words and some gibberish). Next, after waiting a second, open up the console and type `"model.wordSubmissions"`, and you should see an accurate answer for each item's `.isRealWord` property.

#### 16. Add a Score Chip to Each Word

Now that your model is correct it's time to display that information on screen so the user can see.

- In the `wordSubmissionChip` function, we have already created a little "score" chip element, and stored it in the variable called `scoreChip`.
- To make this score chip show up on screen, append it into the larger "word" chip that gets returned from the the function.

*Confirmation:*

- You should see a weird `⟐` symbol tacked onto the end of each word.

#### 17. Display the Correct Content on the Score Chip

Now let's replace the weird `⟐` symbol with the appropriate text content.

- If the submission's word is real, then the content should be the score of the word. You can use the `wordScore` function to determine the score of the word. That function still has an unfinished TODO, so you will always get an answer of `0`, but that's fine for now.
- If the submission's word is not real, then the content should be a capital `"X"`.

*Confirmation:*

- You should see appropriate Xs and 0s, e.g. `honk 0`, `honq X`, `chunk 0`, etc.


#### 18. Style the Score Chip

Still in the same `wordSubmissionChip` function, give the "score" chip the appropriate CSS classes.

- If the word is real, the score chip should have a blue background.
- If the word is not real, the score chip should have a red background.
- In either case, the score chip should have smaller text than the word, and should have a slight margin separating it from the word's text.

*Confirmation:*

- It looks great.

#### 19. Finish Implementing the `wordScore` Function.

Now let's fix those zeros and get the real score showing up next to each word. The problem is that the `wordScore` function is incomplete.

- You have a list of letters in a variable called `letters`. You must map that list of letters into a list of scores, one for each letter, and assign that list into the new variable, `wordScores`.

*Confirmation:*

- You should see a correct score next to each submitted word.

#### 20. Finish Implementing the `currentScore` Function.

This is a rewarding one. You probably noticed that the scoreboard always says 0, no matter what words have been submitted. That's because the `currentScore` function is incomplete!

Notice that it always returns a hardcoded value of `0`. Replace that `0` with the real answer, which is the sum total of all the word scores.

- Notice that you have a list of word scores available to you. You simply have to add those numbers up and return the total.

*Confirmation:*

- You should see real scores on the scoreboard!

#### 21. Finish Implementing the `addNewWordSubmission` Function.

Just one last loose-end to tie up! Currently the user is able to cheat by submitting the same word again and again. Let's fix the `addNewWordSubmission` function so that repeats are rejected.

- The variable `alreadyUsed` is currently hardcoded to `false`. But if the user has already used the word in question, then that value should be `true`. Determine the actual answer.

*Confirmation:*

- If you try to submit the same word more than once, the textbox should simply clear away your text and no new word submission will be added.

---
## Submitting Your Work

You know the drill:

- Commit your changes locally.
- Push your new commit up to Github.
- Head over the *Word Up!* Assignment on Vocareum, and clone your repo.
- Click Submit.
- Victory!!! And all the haters who didn't believe in you are [sore losers][colbert-gif].

[colbert-gif]: http://giphy.com/gifs/OxAMjQW6mmA8g

---
## Extra Credit: All Fired Up

*Coming Soon*
