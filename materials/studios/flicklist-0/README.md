##### Web Track

[Back to Class 0](../../class0)

# Studio: FlickList 0

Welcome to your first Studio! Today is mostly just about getting set up. 

First, you will use Git to grab the starter code for the project. (This will seem excessively complicated--and indeed it is a little more complicated than a normal Git workflow--for reasons that we'll explain later. But don't worry, we will tell you exactly what to do, and help you out if something goes wrong. That's what today is for.)

Next, you will register for an API key with themoviedb.org, an open source database of movies. 

Finally you'll plug your API key into the starter code, and see some immediate results!

### Submit Individually

Today, it is best if you complete this studio on your own computer, rather than with a partner. You are still encouraged to work together with others, but each coder should have their own computer open.

### Gitting Started

On all Studio assignments from now on, you are going to use Git and GitHub for obtaining starter code, working on your code, and submitting it (although you will still submit on Vocareum as well).

Now we are about to to walk you through exactly what to do, with only a minimal amount of accompanying explanation. You are probably going to feel overwhelmed by Git-related jargon. Don't worry! Just try to absorb what you can, and trust that the gaps will fill in over time.

Follow these steps to get started:

##### Make account on GitHub

You should already have made an account while doing <a href="https://guides.github.com/activities/hello-world/" target="_blank">this exercise</a> for today's Prep Work, but if not, <a href="https://github.com/join?source=header-home" target="_blank">make one now</a>.

##### Fork the FlickList Repo

Once you have signed into github, head over to the repository where our class project is hosted: https://github.com/LaunchCodeEducation/flicklist.

To work on this project, you'll need to *fork* your own version of it. Near the upper-right corner of the screen, you should see a button that says "Fork". Click it!

You should now be taken to a new, nearly identical project page. But instead of `LaunchCodeEducation/flicklist`, this is `jharvard/flicklist` (where "jharvard" is your username). 

##### Clone your Fork

Now that you have your own *remote* repository hosted on GitHub, it's time to start working on it. To do so, you will *clone* the remote repo onto your local machine (the CS50 IDE). 

Open up the terminal in your IDE, and type the following:

```nohighlight
$ cd ~/workspace/web-track/studios/
$ git clone https://github.com/jharvard/flicklist.git
Cloning into 'flicklist'...
remote: Counting objects: 103, done.
remote: Compressing objects: 100% (49/49), done.
remote: Total 103 (delta 32), reused 102 (delta 31), pack-reused 0
Receiving objects: 100% (103/103), 17.92 KiB | 0 bytes/s, done.
Resolving deltas: 100% (32/32), done.
Checking connectivity... done.
```

You should now see a new folder.

```nohighlight
$ ls
flicklist
```

Have a look inside:

```nohighlight
$ cd flicklist/
$ ls
README.md  css/  index.html  js/
```

There's some code in here! Open up index.html and take a very brief look. Seems like a lot of stuff. In fact, the entire finished project is all here. See for yourself: open up this page in the browser by clicking preview, or by running the apche50 server and then visiting `ide50-jharvard.cs50.io`). 

Why did we give you the finished product? Well, this is a Git repo, so in fact, the entire history of the project is actually present. To start from the beginning, you just have to go back in time!

We have created 6 *branches* at various points in the history of the project, one for each Studio. You will complete each studio from a different one of these "jumping off points". 

You will learn more about branches in the next Prep Work, but for now, simply follow along blindly like a docile sheep.

##### Add Upstream as a Remote 

In order to obtain the branches we made, your local repo will need a reference to our "upstream" repo, `LaunchCodeEducation/flicklist`. Currently, it only has a reference to your personal "downstream" fork, `jharvard/flicklist`, but not ours. You can see this by asking git for a list of all the remote repos that this local repo knows about:

```nohighlight
$ git remote -v
origin	https://github.com/jharvard/flicklist.git (fetch)
origin	https://github.com/jharvard/flicklist.git (push)
```

Your local repo here has a reference to a remote repo at `https://github.com/jharvard/flicklist.git` (which it refers to as "origin"). But it does not have any references to the "upstream" granddady-of-them-all repo. Let's remedy that:

```nohighlight
$ git remote add upstream https://github.com/LaunchCodeEducation/flicklist.git
```

This says, "Hey git, there's another remote repository that you should know about. Let's call it "upstream", and it lives at this url: https://github.com/LaunchCodeEducation/flicklist.git.

Logging `git remote` again should now reveal that you have a local reference to both of the remotes:

```nohighlight
$ git remote -v
origin  https://github.com/jharvard/flicklist.git (fetch)
origin  https://github.com/jharvard/flicklist.git (push)
upstream        https://github.com/LaunchCodeEducation/flicklist (fetch)
upstream        https://github.com/LaunchCodeEducation/flicklist (push)
```

That's better!

##### Fetch the Branch from Upstream

Now you will *fetch* the branch for today's Studio:

```nohighlight
$ git fetch upstream studio0
From https://github.com/LaunchCodeEducation/flicklist
 * branch            studio0    -> FETCH_HEAD
 * [new branch]      studio0    -> upstream/studio0
```

Next, create a new local branch from the `upstream/studio0` branch:

```nohighlight
$ git branch studio0 upstream/studio0
Branch studio0 set up to track remote branch studio0 from upstream.
```

You now have a new local branch called "studio 0" whose contents came from "upstream/studio0". You can confirm the existence of the new branch by typing:

```nohighlight
$ git branch
* master
  studio0
```

The output indicates that we have two local branches, "master", and "studio0". The `*` next to "master" indicates that master is the branch we currently have *checked out*. 

What does that mean?

##### Check Out the new Branch

To find out, watch what happens when you checkout the new branch:

```nohighlight
$ git checkout studio0
Switched to branch 'studio0'
Your branch is up-to-date with 'upstream/studio0'.
```

Git informs us that we have "switched to" the other branch. If you close and reopen `index.html`, you should see a big change! You might also notice that the `css/` directory has disappeared entirely. And if you preview the webpage in the browser again, you will see that the fancy movie content has reverted to some very basic text.

We have officially time traveled into the past!

##### Make Another Branch for Your Work

The last thing you need to do is make another new branch where you can work on this assignment (we want to keep "studio0" fresh so you can come back to it later). 

Go ahead and create a branch called "studio0-my-work", then look to confirm that it exists, and finally switch over to it:

```nohighlight
$ git branch studio0-my-work
$ git branch
  master
* studio0
  studio0-my-work
$ git checkout studio0-my-work
Switched to branch 'studio0-my-work'
```


### Starter Code

In `index.html`, we have hardcoded some text to appear on the browser screen. At the bottom of the file, notice that we have left a small `TODO` for you, which is to finish our `<script>` tag so that it loads up our local `flicklist.js` file. 

In `js/flicklist.js`, you will see a javascript object stored in a local variable called `api`. 

Below that is a function called `testTheAPI()`, which, true to its name, tests our ability to connect to themoviedb's API. It does so by making making an AJAX request (using jQuery's `.ajax` function) to this url: "https://api.themoviedb.org/3/discover/movie", passing along your API key as a parameter. A success "callback" function is provided to the request, which will be invoked if a response comes back successfully. This callback function will log the response to the console. 

After defining the function, we have a simple `console.log` statement, and then we invoke the function.

That was a mouthful. If any of these terms are unfamiliar to you, know that they are covered thoroughly in Module 8 of CS50, and will be reviewed in your Prep Work for next class.

For today, the only things you need to do are:

1. Fill in the `<script>` tag in `index.html`
2. Get your API key from themoviedb.org (we'll do that next)
3. Paste your key into the code as indicated by the `TODO` in `flicklist.js`


### TheMovieDB API

TheMovieDB is a freely available database of movies and TV shows. We will use their API as the source of our project's data. This API, like most, requires that you register and obtain a key in order to use it. 

Here's how to nab that key:

##### Sign up for an Account

<a href="https://www.themoviedb.org/account/signup" target="_blank">Register here</a>. Then check your email and click the confirmation link.

##### Sign up for API Key

Visit the following url:

https://www.themoviedb.org/account/jharvard/request-api?type=developer

where "jharvard" is your username for the account you just created. Click on the "I agree" button.

##### Register Your Project

You will now be presented with a form. TheMovieDB wants to know about the cool people like us who are using their service. Go ahead and fill the form out. For the project url, point them to your repo on github.

##### Get the Key!

You should now be taken to your profile page, where your key should be visible.


### Your Mission

Again, you have three steps:

1. Fill in the `<script>` tag in `index.html`
2. Get your API key from themoviedb.org (you should have it now)
3. Paste your key into the code as indicated by the `TODO` in `flicklist.js`

Open up the page and see if it works!

### How to Submit

##### Submit on Vocareum

On Vocareum, click on the assignment called **Studio: FlickList 0**.

You should see a file called `studio0.txt`, on which a secret quiz question awaits! Write your anser into that file, and click submit.

##### Commit and Push on Git

If you run the `git status` command, you should see that you now have *unstaged* changes:

```nohighlight
$ git status
On branch studio0-my-work
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
On branch studio0-my-work
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   index.html
        modified:   js/flicklist.js
```

Both files are now staged for committing. Go ahead and make a commit, using the -m flag to remind your future self (and others looking at your code) what changes you made during this commit:

```nohighlight
$ git commit -m "finish FlickList 0 studio"
[studio0-my-work 46db232] finish FlickList 0 studio
 2 files changed, 2 insertions(+), 2 deletions(-)
```

The convention is to write your commit messages using the present tense rather than past tense (e.g. "finish" rather than "finished").

If you check your status one more time, you should see this:

```nohighlight
$ git status
On branch studio0-my-work
nothing to commit, working directory clean
```

Finally, *push* your changes to your remote repo:

```nohighlight
$ git push origin studio0-my-work
Counting objects: 62, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (20/20), done.
Writing objects: 100% (22/22), 2.36 KiB | 0 bytes/s, done.
Total 22 (delta 6), reused 0 (delta 0)
To https://github.com/jharvard/flicklist.git
 * [new branch]      studio0-my-work -> studio0-my-work
```

If you go back and revisit https://github.com/jharvard/flicklist, you should now see your new branch up there!

