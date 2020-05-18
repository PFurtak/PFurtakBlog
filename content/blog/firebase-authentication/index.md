---
title: 'Authentication with Firebase - Why?'
date: 2020-05-18 15:33:20 +0300
description: # Add post description (optional)
img: ./keys.jpg # Add image post (optional)
tags: [Firebase, Authentication, Security]
---

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;There comes a time in your projects when you are going to need to handle user authentication. This is a complex problem to tackle, with many different approaches. In the past I've written my own auth in Node.js and it is a long and tedious process. I've recently learned how to integrate third-party authentication with Firebase into my apps and I have to say, this is a game changer. Like with anything; there are some pro's and con's to using Firebase authentication.

## Pro's

- Ease of use
- Speeds up development
- Offloads complexity and responsibility
- Less barrier to entry for end users
- Potentially more safe for your users
- Analytic data on your users by using Firebase
- Backed by Google

## Con's

- Bringing in outside code
- Reliant on a third party API
- Convenience at a monetary cost
- Less control
- Complex migrations

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In my opinion the biggest advantage to using Firebase for auth is being able to offload complexity and responsibility. The bigger your organization and the better your talent is, this does become less of a factor. Security professionals earn six-figure salaries for a reason, the work is technically complex, and the stakes are extremely high. I've personally seen how ruthless people can be when a security compromise occurs. "Blame-storming" is an all too accurate term, and you do not want any part of that; trust me.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For small teams and personal projects, I see Firebase as a huge asset. For large enterprise applications who have the personnel to handle authentication themselves, Firebase doesn't make as much sense to use. Depending on the scale of the application, it would be much cheaper to have a security professional or team to make sure everything is secure.

## What's next?

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now that we know what Firebase authentication excels at and who is a good fit for it, my next post will be a quick overview on how we can add this to our projects. It is actually much easier to implement than you would imagine. Stay tuned!
