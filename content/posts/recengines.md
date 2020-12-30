---
title: "Recommendation Engines Aren’t For Maximising Metrics, They Are For Designing Experiences"
date: 2015-05-14
draft: false
---

If I hear about the recommendation algorithm one more time I’m going to lose my mind. Framing the conversation like there’s one, perfect, singular rec engine that you’ll be able to find when you come up with just the right algorithm or run just the right A/B test is missing the point. A rec engine is a navigational mechanism and you should treat it like any other tool in your design palette, like colors or page elements or site structures. There are many different recommendation algorithms and the thing that’s different about them isn’t how they maximise your favourite KPI, it’s how they treat the people that have found themselves using your product.
Image for post
Image for post
Between the lines Moonassi

The two dominant rec engine frameworks are user-item algorithms and collaborative filters. User-item algorithms are ten a penny: they typically revolve around a matrix that has users (you know, people) as rows and items — books, articles, films, whatever — as columns. To get a recommendation for a user you perform some linear algebra or some Bayesian modelling or something to get items similar to ones the user has bought, or read, or watched, or whatever. Collaborative filters are the ones that power “people like you also bought” type of recommendations. The algorithm finds a cohort of people “like” your user, sees what they have in common, and recommends that thing the cohort has in common, but your user doesn’t.

There are lots of variations on these themes but the details truly don’t matter in any way but one: what matters is how you treat people.

Think about how these algorithms affect your users. How do you want to find people “like” me? Other white men in their thirties from Brooklyn? Other people that spend their time vegetating in front of “Veep” and writing code? Or how about people that also wish they could ride their bike to work down a country lane in Yorkshire but actually commute on the subway under Manhattan? If you chose one of these collaborative filters over the other what does that say about how you think about your users? How does that expose your values?

This is design. Sacrificing design decisions to the whim of some A/B test means that all you will have left to design are your KPIs. Spending your talent (that should be spent on thinking about desires and aesthetics and behaviors) on populating A/B test buckets will leave you with nothing apart from a strong need to really nail that engagement definition once and for all. You will have left your design to the vagaries of the data scientists who will take their favourite metric (mine’s a Hamming distance) and figure out how to apply that to your problem of return purchases, or time on page, or completion rate, or whatever. And you’ll spend time designing options that win the A/B test battle, only to find that you’re now recommending listicles to the same fake phone-verified Facebook accounts that visited your A/B test in the first place.

A/B tests for design are just ways of not making choices. Leave tests to the market researchers; they will not help you.

Rec engines should be thought of as tools in a design palette. Choose one algorithm if you want to think about your user’s sequence of actions, choose another if you want to think about the weather in their locale. The algorithms just mean that the experience you design can be (even) more exciting, or interesting, or ugly or beautiful or whatever it is you’re aiming for. Your choice of algorithm isn’t science: it doesn’t absolve you from making other, real choices. There are no fundamental rules of taste or behaviour or desire that you’re trying to uncover, no truths that will still be truths next week or next year. There is only how you treat people.
