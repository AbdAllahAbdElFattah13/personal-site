+++ 
date = 2021-08-16T12:48:20+03:00
title = "Thoughts on legacy code, rewriting from scratch and bussines requirements..."
description = ""
slug = ""
authors = []
tags = ["legacy-code"]
categories = ["software-engineering", "clean-code", "bussines-engineering-relations"]
externalLink = ""
series = []
+++

A friend has a question:
> Instead of trying to refactor a legacy system, why not building it again from the ground up? In both cases I'll likely need to rewrite 90% of it again to follow clean code principles!

I liked the question, so I decided to attempt to answer it as follows:

Your questions has lots of hidden assumptions in it, I’ll try to clarify some of them down below:

- You’re assuming that you know and understand all of the legacy system functions to the point that you can rebuild from scratch. In 90% of the cases this isn’t correct, the word “legacy system” doesn’t just mean that it’s an old system (i.e working from (x) number of years), it means lots of things including that the system have some “hidden” functionalities that still working somehow. So in 90% of the cases you don’t fully know/understand the use cases in this legacy system to be able to build from scratch.
- You’re assuming that you have the time to create the system from the ground up, in most cases this isn’t true, because usually the business side has a pipeline of ideas that it wants to do or try out to increase the profitability, that in case you’re working in a product team. In case of working in a company that build SW for other customers, this time is literally worth money! The time to re-build this system can be used to build 3 new ones for new customers worthing more money, also remember that you need to convince the customer with the need for system rebuild, which not an easy challenge.

- You’re forgetting the scale of the legacy system, legacy system are bing built for years, so it might needs a smellier amount of time to rebuild it. (This isn’t always true, but it exists in some cases)

- Your customer (either the business side in your company or another company) usually doesn’t see the problems of the nasty code, for them the system is up and running! This (Communication between SW Engineers and Customers) is one of the hardest problems to solve in our industry. In such cases you need the Customers what makes a code clean or nasty, why is nasty code is bad in longer runs, and what’s their gain for them in case if we have a better codebase. You need to do all of this while you’re still adding more features to the existing legacy system, or fixing bugs. It’s really hard to go on to a customer and tell him: Hey, we need 6 months to build the system from the ground up, in this time we won’t be adding any new features or bugs to the system, and in the best case scenario: You’ll get the same system again. To a customer (one who doesn’t understand the above mentioned points) those are 6 months of wasted money and efforts. Why on earth would someone do this?

Well, that's what I have on that now, I'll add more articles if I felt the need. : ))
