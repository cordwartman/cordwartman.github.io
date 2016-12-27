---
layout: post
title: BlocChat
thumbnail-path: "img/blocchat.png"
short-description: BlocChat is a simple chatroom setup for users to communicate between each other.

---

{:.center}
![]({{ site.baseurl }}/img/blocchat.png)

## Summary

While the industry doesn't need anymore full chat solutions, a local integrated chat function can be usefull for inter-company chat or customer service. So learning how to design one was a fun project.

## Explanation

This was the second of my two front-end projects, using Firebase and AngularFire I was tasked with designing a chat room site with many different functions.

## Problem

The first task was to design the wireframe of my chatroom site and make some design decisions about where I wanted to put each element.

My next task was to setup a list of chatrooms in the Firebase database and to display that list on the site, it needed to update dynamically as chat rooms were added. This led to another step, allowing users to create chat rooms. 

Users needed a way to set their username, send messages, and then messages would need to be assigned to those usernames and the respective room. The messages would then need to be update dynamically and be assigned to the proper room.

## Solution

The design of the site was an ever evolving process and with each new element things had to be adjusted to fit the element or to make sure the page flow was not disturbed. 

Setting up the list of chatrooms was fairly straight forward, using `$firebasearray` the list of chatrooms could be referenced just like an array and with Angular's `ng-repeat` directive the chat rooms would update as they were created.

To allow the creatation of the chatrooms I used `ui-bootstrap` and the `uibmodal` service to create a modal that accepted new room names and then used `$firebasearray` to add the new chatroom to the database.

Creating a Username also used the `uibmodal` service but the name was stored using the `ngCookies` module to save the user name to the user's local machine. To save messages each message was saved to the database using `$firebasearray` and was assigned a reference for roomId, content, username, and a timestamp.

Using Firebase allows for quick data exchange between the database and the webpage, which is important for an efficient chat room. The `uibmodal` service was a quick and efficient solution for asking for inputs from the user and in the case of the username it offered settings to setup a sort of gateway to the chat rooms before a user can start using it.

## Results

Most of the chat site worked just as designed, messages could be sent, chat rooms created, and usernames assigned. There were a few design problems and a few database organization issues. 

## Conclusion

Some things needed some polish to be considered acceptable for a more user friendly chat room experience. One of those was to enter messages the user has to click the Send button and then erase the input field. 

Something I would have done differently from the start would have been to start my design with a better idea of how the page would work on mobile devices. 

Another thing I would have done differently would be to organize my messages differently. The way we were instructed to organize them was all under one section of messages and then to query them by their room Id. My mentor pointed out that once Firebase databases get too big it becomes very load heavy to query them. A better solution would be to save the messages of each room under the room object and then to order them by timestamp. Using this organization you wouldn't have to query the messages just use an order method and `ng-repeat` to put them in the message field.

I feel like I learned a lot of practical applications with the tools I used to make this project and learned how different databases worked. I also obtained a better understanding of how Angular's MVC works.