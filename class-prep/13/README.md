---
title: "Class 13 Prep"
---

Before coming to class 13, please complete the following tasks:

### Studio Recap

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|-------------
Follow Along | Exercise | 30 minutes | [FlickList 5 Solution](https://github.com/LaunchCodeEducation/flicklist/tree/studio5-staff-solution) | Read over (and maybe even code along with) the staff solution to the previous Studio, so that you're up to speed with the starter code for the upcoming one.


### Firebase (Optional)

So far, for the entirety of this Front-end skill track, we have been writing client-side code that runs in the browser on the user's computer. But if you make a project that only contains a front-end, and no back-end, you lose a very big feature: saving user data. Normally, in order to persist (non-trivial amounts of) user data, your app needs both a database and a back-end in addition to the front-end. But that's annoying, because it means you have way more work to do!

Firebase is a service that provides a back-end for us. The idea is that Firebase does most of the heavy lifting, and we simply connect to Firebase using AJAX calls whenever we want to save or retrieve data.

Firebase is **not** necessarily an essential skill that you must have in your toolkit in order to be a competitive candidate for a front-end job. But if you have a project idea that requires you to persist user data, and you don't want to build out the entire full stack yourself, then you might find Firebase useful.

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|-------------
Install | Website | [NodeJS website](https://nodejs.org/en/) | 15 minutes | Follow the instructions to download and install NodeJS. NodeJS is a Javascript interpreter and "runtime environment". Basically, it lets you run Javascript outside of the browser (like in your terminal, for example). <br><br> The reason you are installing Node is that it also comes with a "package manager" called [NPM](https://www.npmjs.com), which is a command-line tool that you will use to install *yet another* command-line tool, [firebase-tools][firebase-tools-npm]. Yay, install fest! Your favorite part of programming.
Read / Follow-Along | Docs / Tutorials | [Firebase Docs][firebase-docs] | 3 hours | Go through some of the tutorials on the docs page. Firebase was recently acquired by Google, and they have subsequently made some changes, so unfortunately much of the other learning materials out there on the web are now out of date. But there is a lot of decently human-friendly content on this documentation site.

[firebase-tools-npm]: https://www.npmjs.com/package/firebase-tools
[firebase-docs]: https://firebase.google.com/docs/web/setup
