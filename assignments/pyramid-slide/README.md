---
title: "Pyramid Slide"
---

<img width="600px" src="https://www.carnival.com/~/media/Images/PreSales/Excursions/Ports_M-Q/NAS/424042/Pictures/atlantis-dolphin-cay-deep-water-swim-and-aquaventure-nassau-the-bahamas-13.jpg"/>

^ That's how much fun you are about to have.

## Your Task

You've been working at Mario Inc for awhile now, and during Studios you have continually iterated on your product, shipping better and better Pyramids.

Today your team's designer, Daisy, came to you with a new UI design and some new features that are surely going to take the company to the next level.

Daisy has mocked up an animation of the functionality she envisions:

<!-- <img style="width:800px" src="http://g.recordit.co/QBknlRbuSe.gif"/> -->
![mockup](http://g.recordit.co/QBknlRbuSe.gif)

Your task is to make it real!

> *NOTE:* If the image above fails to load, then [click here to see Daisy's mock-up][daisy-mockup].


## Setup

1. Make a [new repository on Github][new-repo]. Give it the name `"pyramid-slide"`.
2. Clone your repository down onto your computer.

> *NOTE*: If you need more guidance on this process, see steps 1 and 2 from the [Getting Started][getting-started] Assignment from the Unit 2 Python course.

## Notes and Tips

A few tips before you start:

- Don't worry about styles or layout until you are done with all the functionality.
- A "slider" is actually just an `<input>` whose `type` attribute is equal to `"range"`. See [here][input-range] for more details.
- The slider event that you care about is `oninput`. See [here][oninput] for more details.
- Remember that a dropdown menu is just a `<select>` element with some `<option>` elements nested inside.
- The select event that you care about is `onchange`.
- You will need to use the following style attributes:
    - `margin`, `padding`, `color`, `background-color`, `border`, `border-radius`, `font-size`, `font-weight`

Ok, you are all set. Go make that pyramid!

## Submit Your Work

In order to submit your work, you will need to push your project up to GitHub. Follow the steps below:

1. First, `add` and `commit` your changes.
2. Now your local repo is one commit ahead of your remote repo (the one that your created on Github.com). To sync them, `push` your local changes up to the remote:

    ```nohighlight
    $ git push
    Counting objects: 3, done.
    Writing objects: 100% (3/3), 213 bytes | 0 bytes/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To https://github.com/bobthebuilder/pyramid-slide.git
     * [new branch]      master -> master
    ```

    Now if you revisit github.com/bobthebuilder/pyramid-slide in the browser (but substitute your own username in place of "bobthebuilder"), you should see your latest code in there!

## Woo!

Congratulations on conquering the Pyramid Slide!

Time to enjoy a cold one:

![kool-aid](http://i.imgur.com/pmC3Kch.gif)




[dolphin-cay]: https://www.carnival.com/~/media/Images/PreSales/Excursions/Ports_M-Q/NAS/424042/Pictures/atlantis-dolphin-cay-deep-water-swim-and-aquaventure-nassau-the-bahamas-13.jpg

[daisy-mockup]: http://recordit.co/QBknlRbuSe

[getting-started]: http://education.launchcode.org/web-fundamentals/assignments/getting-started/

[input-range]: http://www.w3schools.com/html/html_form_input_types.asp

[oninput]: http://www.w3schools.com/jsref/event_oninput.asp
