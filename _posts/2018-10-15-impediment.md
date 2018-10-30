---
layout: post
title: im·ped·i·ment
---

> "The minute you want to complain about something is the minute you should start peeking under the hood. You're ready." - Dan Abramov

It was a quote from Dan's tweet, he posted a poll and was asking this question — _If a library is unmaintained and prevents you from upgrading React for many months, what do you do and why?_

It's not that far from my current issue but the quote struck me. Though not totally related since I'm not working on a ReactJS project now, I just happened to relate my current circumstance with his tweet. I realized that I've complained a lot and had a hard time dealing with my current project.

The project's an [ESL](https://en.wikipedia.org/wiki/English_as_a_second_or_foreign_language) system that offers an instructor to student video conferencing feature. Easy, right? Nope. Aside from the fact that I don't have any experiences with video conferencing APIs before, I was only given a two month period (three max) for this. It was supposed to be built with a [Wordpress](https://wordpress.com/) plugin to comply with the time constraint and scope. But unfortunately, the one we found and paid for wasn't actually a plugin but a PHP script built with [CodeIgniter](https://www.codeigniter.com/). Now that's another problem for me, though I have a fairly good amount of knowledge with [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) and [Laravel](https://laravel.com/), I don't have any experience with CodeIgniter's approach or its code. For a quick solution (at least I thought that it was), I suggested that we should look for an alternative pre-constructed system that has the same features but should be built with something that I have experience with. We found one that has a lot of features and even included most of the project's specs, it is made with Laravel and [AngularJS](https://angularjs.org/).

That's nice, happy coding then!

Sorry to spoil the almost _"yes!"_ but **no**, the codebase is a mess. It's all over the place, no artisan, no eloquent, most of the packages that made Laravel the _"go-to"_ framework for PHP developers were all thrown away. Heck, even the default directory structure has been tampered with. And, you might say this — "Well at least the frontend's fine right?" That's another no for you, we all know that AngularJS is history and I'm coding with an older version of it alongside its outdated documentation.

_Moving on._

I failed to accomplish my tasks on time for the first sprint. It is driving me mad, but then I took a deep breath and asked the product owner for a short meeting to raise my concerns about the issues I'm having. Luckily, the product owner is our CTO, she's very busy but she gave the meeting a go. I addressed my problems about the codebase and told her all of the things I hate about it. It was a compromise on my end. She listened to me, and after sharing those to her, she immediately took the initiative to look at the code herself and told me that she know that version of AngularJS. In addition, she also said that I can always message her on Slack if I get stuck again so that she could help me out.

It was the best decision I made so far in this project.

I learned a lot that day, she taught me how should I consume the api endpoints with AngularJS's [scope](https://www.w3schools.com/angular/angular_scopes.asp) and how to tackle other bugs that I encountered before. After that, I smiled and gave my thanks to her. And, I'm still learning, the key takeaway about this is that you should confront the situation, address it, and then handle it. Asking for help doesn't mean you're incompetent, if you think this way, you will just miss out the chances that you might have missed by not asking. If you have issues with a monolith's codebase, just fix it yourself, don't dwell on it.

I think this is one of those "lessons" that is learned the hard way. That's it for tonight. Happy coding!