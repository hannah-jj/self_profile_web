---
layout: post
title:  "First Gem and K.I.S.S"
date:   2017-02-20 23:48:10 -0500
excerpt_separator: <!--more-->
---


2/20/2017 will always have a special place in my life journey going forward, because it is the day that I published my first Gem!!! <!--more-->You can celebrate the occasion with me by typing below into your terminal:

```
$ gem install countries_of_the_world
```

to run the app, type below:

```
$ countries_of_the_world
```

Below is the story of how to build a Gem, should you accept the mission to read on, you will find out what KISS is as well:

## **Building a CLI Data Gem in 5 Steps**

1: Decide on a website to scrape information from:  travel the world is on my will-do-list, so I found a website that has basic information on each country conveniently located in one place - [worldbank](http://www.worldbank.org/en/country)

2: Download the files needed to build a gem by typing "bundle gem name_of_gem" in your terminal. Detailed instructions on how to use bundle to build a gem is located here - [bundler - creating_gem](https://bundler.io/v1.13/guides/creating_gem).

3: Code away!!!

hours and hours of coding later...

4: Once your codes are bulletproof, update the .gemspec file wherever that says "TODO" and most importantly the below line:

```
spec.executables   << 'countries_of_the_world'
```
This line tells Gem to run the executable file that is named countries_of_the_world located in the bin file when user starts your program. (This step took a lot of googling...... why can't they put that in the instruction... )

5: Test the gem locally & then publish to [rubygems.org](https://rubygems.org/) be sure to sign up for an account on the website ahead of time

```
$ rake build
$ gem install pkg/whatever_the_gem_created_in_rake_build
$ countries_of_the_world (or whatever your executable is)

$ rake release
```

***Done!*** eat a cake, and then start writing blog, and/or record video of walk-thru

============================================================================================================

# **Step 3 elaborated:**


Coding took the most amount of time in the whole project. And the principle I follow is KISS - Keep It Simple Stupid.

# Design

**Scraper Class** - scraps information from web pages and return hash or array to the caller

**Country Class** - retains and displays the information related to countries

**CLI Class**  - controlling the overall i/o and the other two classes.  It calls scraper class to get info from web page, then tells country class to store and retrieve the information as needed by the user.

I originally wanted to keep the two classes completely separated, b/c that's the point of OO. Each object is like a black-box, which has no awareness of the outside world, other than getting input and spitting outputs.  

However, scraping the information for 181 countries along took a whole minute to complete in scraper class. If I kept that route and let country class take the information and build up the whole world containing all countries, it would take another minute. User may just quit my program if the app was idle for so long. So I decided to take a shortcut:

Scrape Class:

**scrape_page method** - scrapes only the name and url of each country and creates each country object as it scrapes.

**country_page method** - scrapes detail information of a country only if the user tells CLI class to display details of that country.  So the information is pulled on the fly and takes only a couple seconds to display.

Other than scrape_page method has crossed over the boundary of my original design, everything stayed as a simple and stupid (but elegant) black-box.

# Broken Links
It turned out that scraping is the easiest part of the coding process.  Dealing with broken links took most of time. And there were a lot of broken links for website with lots of information!!!  I had to google a lot to find out how to find out when a link is broken without me manually clicking over all the links:

```
    uri = URI.parse(url)
    result = Net::HTTP.start(uri.host, uri.port) { |http| http.get(uri.path) }

		if url.include?("capeverde") #cape verde page will return 302, but the link is actually broken
			[nil,nil]
		elsif result.code.to_i >= 200 && result.code.to_i < 400
			doc = Nokogiri::HTML(open(url))
			[doc.css("li.come-level a.toggle strong").text,
			doc.css("li.region a.toggle strong").text
			]
		else
			[nil,nil]
		end
```

When the response code from the Net::HTTP is anything lower than 200 or higher than 400, it's a broken link. (Damn 404!!!)

# Celebrate
Now that you've reached the end of this blog post, feel free to celebrate a little too.  Here is link to my github for your viewing pleasure:

[link to github](https://github.com/hannah11361/countries-of-the-world-cli-app)

I noticed that the i/o for music library project used "colorize" gem, so I got obsessed with the colors too. (If you install my gem, you will see the welcome screen blinks!!! That was as easy as typing .blink after any string. Have fun! Get a cake and you can eat it too!

![](http://i.imgur.com/ClbtwNy.png)
