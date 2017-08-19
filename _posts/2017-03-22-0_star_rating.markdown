---
layout: post
title:  "0 star rating"
date:   2017-03-22 01:54:46 -0400
excerpt_separator: <!--more-->
---


For starters, I am too nice to give anything 0 star rating, but I've always wonder why website can't let user give 0 star?  <!--more-->It comes handy if there is something that truly deserves a 0 star.  For my sinatra project, I've build an app that let user rate movies.  Yes, rating movies are all over the web, from imdb, to netflix, to amazon, to everywhere movie is mentioned, but I haven't found one that allows 0 star!!! Developers certainly are kind-hearted.

**Gems:**

The app requires the usage of several skills which we learn throughout the courses leading up to the project: ActiveRecord, Sinatra, Rake to name a few. (Ironically, I've searched the web for a couple hours on how to clean up a database and reset the primary ID to start from 1... and I have just noticed in the Gemfile as I am typing this blog, there is a gem called "database_cleaner". ) .  Nonetheless below is the fruits of my hours of research:

```
Movie.destroy_all
ActiveRecord::Base.connection.execute("delete from sqlite_sequence where name = 'movies'")
```

Substitute Movie for your model and movies for your table.

**Database**

three tables: users, movies and ratings
relationship: a user has many ratings, a movie has many ratings, only one rating per movie per user allowed.

**Web Scraping For Fun**

I've utilized web scraping skills to conveniently scrape some movie information from www.imdb.com to populate the movie table.  I've noticed that all of imdb.com's page that contains list of movies follow the exact same structure (as expected), so I can now scrape any imdb page that consists of list of movies, just by changing the link in the method.  Check out [the movie.rb and seeds.rb](https://github.com/hannah11361/sinatra-app-wikimovia) for details.

**Pink and Purple Rule the World**

BTW I've rated Beauty and the Beast 5/5 as shown below. It is so good that my friends went to see it twice with 3D.

![Wikimovia Screenshot](http://i.imgur.com/gt3AeVo.png)
