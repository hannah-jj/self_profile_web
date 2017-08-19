---
layout: post
title:  "Rails Project : Let's Go"
date:   2017-06-24 02:05:37 -0400
---


Completing the portfolio project on rails marks a significant milestone on this journey of becoming a web developer.  As a fellow student mentioned, I no longer feel like a fake developer after completing this project.  

**Planning**

Summer is the season of gathering.  As friends plan out gathering events, I immediately clicked and wanted to build an app to organize events. 

**Features**

- Users can organize events, add itineraries to the events, exchange comments and note their participation of "yes, maybe, no".  
- Guest has the luxury of browsing all events. 
- There is a special feature that will displace events ranked by participations.  The most popular ones are the defined by the most "yes".  

Those sounded like fairly easy tasks with such limited features, but the models and controllers were already getting very complicated.  This really make me appreciate more on all the beautiful websites out there having much more complexities.

**View**

Once the main features are decided, I drew the views and layouts of each pages.  The main actions are:
- an event's show page which shows the details of the event, list all the itineraries and comments associated.
- a user's dashboard showing events as organizers & events as participants.
- a most-popular-events page featuring detail statistics of all participants' responses

**Associations**

With the end goals in sight, it was easy to draw the relationships between models and map out the associations:

- event 
     - belongs to an organizer (user)
     - has many participants (users) through the relationships with event_users, a join table recording an event, a participant & a participant's response (yes, maybe, no)
     - has many comments
     - has many itineraries
     
- user
     - has many meetings (as an organizer)
     - has many itineraries through meetings as an organizer
     - has many events (as a participant)
     - has many comments

- comment
     - belongs to an event
     - belongs to a user

- itinerary
     - belongs to an event

**The Look**

Though the website obviously shows the developer behind it is an amateur, I actually spent 25% of time making it look reasonably eye-pleasing.  I utilized free css template found on this page:
[Bootswatch](https://bootswatch.com/simplex/)
I was obsessed with getting the buttons to fade out when a user clicks and responds and the little badge with number will update correctly, hours and hours on getting this feature to work.

here is how it looks before a user responds to an event:
![](http://i.imgur.com/g2QzDhG.png)

after clicking yes

![](http://i.imgur.com/73r1CjX.png)

changing the response to maybe

![](http://i.imgur.com/DJyRvqN.png)

**Authentication**

Third Party login took many hours. And I gave up on getting google login to work, Facebook login with devise was much easier with the help of this website:
[www.adrianprieto.com](https://www.adrianprieto.com/how-to-setup-devise-and-omniauth-for-your-rails-application/)

I struggled with invalid credential for 2 hours and finally determined that somehow the app wasn't passing the Facebook app id and client secret correctly during callback.  I verified the codes in console was stored properly in ENV variables, but somehow it was still not working. I took a shortcut of just storing the key and secret directly in the config file. This is definitely not recommended for real website.

**Naming Convention**

Many hours were spent on associations, but not because of complexities, rather the naming convention.  The join table was named as event_user (I should have just chosen one word in hindsight).  For the longest time, I wasn't able to get the association to work no matter what variations I have tried.  After hours of googling and reading lessons again and again, it finally clicked that instead of finding the right way to name the plurals of table with two words, I can just add class_name:

```
class Event < ApplicationRecord
  
  belongs_to :organizer, :class_name => "User"
  
  has_many :event_users, class_name: "Event_User"
  has_many :participants, through: :event_users
	
```

**Celebration**

It's done and I am proud & sleep deprived.

For your viewing pleasure: [https://github.com/hannah11361/io-let-us-go-rails-project](https://github.com/hannah11361/io-let-us-go-rails-project)




      
