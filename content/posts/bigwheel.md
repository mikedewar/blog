---
title: "Bigwheel"
date: 2013-11-25
draft: false
---

I wrote this toward the end of 2013 while I was working at the New York Times R&D lab and was exploring ideas around how to work with live data. Now, after a few years of working with "real" e.g. non-media data this post seems awfully naive. Nonetheless there are a few ideas here that I still enjoy - streams as a common mechanism for data distribution, and data scientists managing their own stores of data. 

I'm capturing it here for posterity.

---

# The Big Wheel Data Science Manifesto

The age of receiving data as a static, curated CSV file is over. The basic unit of analysis of data science is the stream, and by providing researchers and product developers with playful access to a selection of data streams they can be at their most effective. 

The data scientists in your organisation are absolutely dependent on the data they have access to. They need unfettered access to data, to as much of it as possible. They’ve got the skill to process it, to join it together, and beat it into whatever shape they want. They can store it themselves, use it to build models themselves, and make visualisations themselves.  But, to do any of this, they need access to the data in the first place.

Here’s the rub, though: your data scientist has no clue at all what they’re going to do with the data. They are trained to dive into data and to discover those patterns that may or may not be present and there’s no way they know what’s in there before they get going. Their access to data, then, must  be protected from the rigours of production systems. 

For example, your data scientists are going to break things. They are probably going to reach too far and do too much computation over too much data. It’s OK, they’ll learn a lot in the process, but this is not a positive process if they just broke a production system.

This is where streams come in. All data arrives in one way or another: we get streams of tweets from twitter, check-ins from foursquare and clicks from bitly. We get RSS feeds of posts from our favourite newspapers and blogs; we get live stock prices from wall street and temperature data from our thermostats. Our servers fill up with log files where each line describes the miniscule details of browsing behaviour on our sites. The age of receiving data as a static CSV file is over - and this is a great thing because by focusing on streams of data we can provision access to data for research in new ways. 

A data scientist in 2013 works with an entirely new set of tools compared to their forerunners of five to ten years ago. The ease with which custom, project-specific stores can be instantiated using tools like Amazon’s Web Services or OpenStack is nothing short of amazing. This means that a data scientist can stand up a custom store, be it an SQL or NoSQL store, on disk or in-memory, in a matter of minutes. They can build these stores using stand-alone products like Amazon’s DynamoDB or Redshift, or stand up their own cloud-based machines and install MongoDB, Redis or Cassandra themselves. Algorithms for cleaning, analysing and visualising data can be performed on these same machines. All of this can be done quickly and cheaply, and can all be torn down in moments if it no longer useful. 

The only thing missing from this picture is the data. By shifting the responsibility of storage onto the data scientist all an organisation need do in order to make their data scientists most effective is provide access to streams of data. A stream of data is a (potentially) never ending sequence of messages - be they pageviews, tweets, temperature readings or stock prices. The data scientist doesn’t need a complicated RESTful API, a central data warehouse or a networked file system. They simply need the ability to tap into a stream of data and run with it. 

Using systems like bitly’s open-source NSQ (https://github.com/bitly/nsq), the necessary software can be put into place that allows:
A data menu: the software provides a catalogue of all the possible data sources that are made available by your organisation for the data scientist to work with.
Playful access to data: the data scientist can pick and choose the data they are interested in, without having to justify it ahead of time.
Robust access to data: the software can be configured to allow the data scientist to mess up spectacularly without damaging the other users of the system (in stark contrast to a production system where the exact opposite should be true).
Decoupling of production and research systems: the production systems are only responsible for emitting a stream of data; where it goes after that is of no concern. 

A data scientist, bent on answering the latest analysis question or building their latest data-driven product prototype, then simply hooks into this system, chooses which data they’d like to work with, and simply starts processing and storing that data. No usernames or passwords had to be set up, no complex queries had to be written, and no meetings justifying how the data is going to be used had to be scheduled. 

By focusing on providing access to streams of data, rather than heavily regulated access to production systems and archives, an organisation is able to fully empower their data scientists.

