# Class 5 Prep

Before coming to class 5, please complete the following tasks:

### Talking to the Outside World

Thus far, you have only seen Javascript contained in a relatively sheltered bubble, cooped up inside the browser sandbox. Aside from using the DOM to communicate with the user, or using `console.log` statements to talk to the coder, your Javascript code is isolated. Today you will see how Javascript can make HTTP requests to talk to the rest of the world.

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|--------------
Read | Interactive Book | [EloquentJS 17 -- HTTP][eloquent17] | 4 hours | This chapter is difficult, but the key takeaway is the following: <br> You can send HTTP requests from within Javascript. This is great because it means you can fetch and send data without refreshing the page. But doing so requires *waiting* for the response to come back, and in the meantime you don't want your whole page to be paused and unresponsive. The solution is to use something called a "callback" function to designate a piece of code that should only be run later, once the response has been received. A callback is a function that gets passed in as an argument to another function.
Read | Interactive Book | [EloquentJS 18 -- Forms and Form Fields][eloquent18] | 2 hours | This chapter talks about HTML forms and gives a brief survey over all the different kinds of input elements you can wrap inside a form.


[eloquent17]: http://eloquentjavascript.net/17_http.html
[eloquent18]: http://eloquentjavascript.net/18_forms.html
