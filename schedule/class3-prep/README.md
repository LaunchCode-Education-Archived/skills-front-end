
# Class 3 Prep

Before coming to [Class 3](../class3), please complete the following tasks:

### Responding to Events

We have seen how to use Javascript to modify the DOM, but so far the interaction has been a one-way street, with us (the program) doing stuff, and the user just sitting there watching like it's TV. In order to make our web page *interactive*, we need a way of responding to actions coming *from the user*. We want to be able to say, for example, "when the user clicks that button over there, here is what should happen: ...". To allow us to do that, Javascript "listens for events" such as button clicks, and provides an interface for us to specify functions that should be invoked whenever the event occurs.

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|-------------
Read | Interactive Book | [EloquentJS 5: Higher-order Functions][eloquent5] | 3 hours | In order to start writing event handlers for the DOM, you will first need to get comfortable with the concept of a "higher-order" function: a function that accepts *another function* as an argument, or returns another function as its return value. Higher-order functions are somewhat mind-bending at first, but allow for very elegant solutions to all kinds of problems, and in fact are the foundation of a whole area of programming called Functional Programming (which is awesome and you should check it out later).
Read | Interactive Book | [EloquentJS 14: Handling Events][eloquent14] | 3 hours | Now for the fun part! In this chapter you will see examples of a bunch of different types of events you can listen for.
Read | Article | [Javascript's Map, Reduce and Filter][map-reduce-filter] | 30 minutes | This article talks about some very common higher-order functions for operating on lists: `map`, `filter` and `reduce`.


[eloquent5]: http://eloquentjavascript.net/05_higher_order.html
[map-reduce-filter]: https://danmartensen.svbtle.com/javascripts-map-reduce-and-filter
[eloquent14]: http://eloquentjavascript.net/14_event.html
