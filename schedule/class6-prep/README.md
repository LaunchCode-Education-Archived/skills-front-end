
# Class 6 Prep

We are now transitioning to a point in the class where we will be making a bunch of HTTP requests to external servers, and processing the data we receive back. This, of course, is what a browser does every time you visit a webpage. But in fact, there are other ways of making HTTP requests. On the front-end, one very common technique for making requests is using a technique called AJAX, which you will learn about in the Udacity course below.

Before coming to [Class 6](../class6), please complete the following tasks:


### cURL

cURL is a command-line tool that lets you simply make HTTP requests and see the response. This is a helpful tool for debugging, and for playing around the APIs of third-party sources that make their data available (like in the Udacity course below).

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|--------------
Follow-Along | Article | [cURL Tutorial][curl-tutorial] | 30 minutes | As you read this article, make sure to open up a Terminal window follow along with the examples.


### JSON

When sending and receiving data, there are a variety of different standards for the exact syntax of how to structure the data as text. These days, the most common standard is JSON.

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|--------------
Read | Article | [What is JSON: the 3 minute JSON Tutorial][3-minute-json] | 3 minutes! | This (very old) article gives a quick intro to JSON.
Read  | Stack Overflow Post | [What is JSON and Why Should I Use it?][what-is-json] | a few more minutes | Quickly read this SO post on JSON.

### AJAX

In Javascript, you can make a request to a server, wait for the response to come back, and then do something with the response, without the user ever having to leave or refresh the page. This technique is called AJAX. This is how Gmail, for example, makes your newly received email appear instantly in your inbox, even without you refreshing the page.

Task | Resource Type | Link | Time Estimate | Instructions
-----|---------------|------|---------------|--------------
Do   | Interactive Course | [Udacity: Intro to AJAX][intro-to-ajax] | 6 hours | This course covers the basics of making AJAX requests. You will see how to build a project that reads data from third-party services like Google Maps and Wikipedia by making AJAX requests to those sites' publicly-facing APIs.




[curl-tutorial]: http://www.yilmazhuseyin.com/blog/dev/curl-tutorial-examples-usage/
[3-minute-json]: http://www.secretgeek.net/json_3mins
[what-is-json]: http://stackoverflow.com/questions/383692/what-is-json-and-why-would-i-use-it
[intro-to-ajax]: https://www.udacity.com/course/intro-to-ajax--ud110
