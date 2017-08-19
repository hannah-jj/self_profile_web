---
layout: post
title:  "Rails Project - with JQuery & JSON"
date:   2017-07-15 11:50:03 +0000
---



It has been an amazing journey to see how websites are born and transformed into functional applications that can do almost anything. We are bound by our own imaginations, or how much time you are willing to spend googling!

**planning**

- render events index, show & user show page with json backend

- event show page contains buttons to advance to next event, load statistics (numbers of people going/not going/maybe going), load associated itineraries & comments.

**action**

- customize Active Model Serializer for each model to fit the format desired for easier rendering

```
class UserSerializer < ActiveModel::Serializer
  attributes :id, :name, :email, :meetings, :events

  #user organized meeting
  def meetings
  	object.meetings.map do |meeting|
  		{id: meeting.id, attributes: {title: meeting.title}}
  	end
  end

  #user particiating event
  def events
  	object.events.map do |event|
  		{id: event.id, attributes: {title: event.title}}
  	end
  end
end
```

- tackle one view page at a time, but plan ahead since some pages can share the same template. For example: list of events on event index page and user show page utilize the same handlebar template
- have fun with the ajax $.get and $.post

```
function loadItineraries(){
	var event_id = parseInt($(".js-next").attr("data-id"));
	$.get("/events/" + event_id +"/itineraries.json", function(data){ 
		var itinerariesHTML = HandlebarsTemplates['itineraries']({itineraries : data["data"]});
		$(".itineraries").html(itinerariesHTML);
	});	
}
```

- have fun using Javascript Model Objects:
```
//declare Comment object
function Comment(id, event_id, email, comment){
	this.id = id;
	this.event = event_id;
	this.comment = comment;
	this.email = email;
}
// prototype function for Comment Object
Comment.prototype.newComment = function() {
	return (`<tr class="info">
			<td>${this.comment}</td>
			<td>${this.email}</td>
			<td align="right"><a class="btn-info" href="/events/${this.event_id}/comments/${this.id}">view</td></tr>
		`);
}
```

**wrap up**

breath and celebrate!

**some random tips:**

**pictures**

A picture is worth a thousand words. 

![pictures](http://i.imgur.com/ID9yl2T.gif)

Place picture for rails application under :
``` #app/assets/images ```

use /assets/leave.jpg as url since rails knows images are contained in the images folder.

[List of websites with free beautiful stock photos ](https://blog.snappa.com/free-stock-photos/)

[make moving photos (gif) on this site](http://gifmaker.me/)

**handlebars template in rails**

An example walk-thru is worth a hundred google searches:

[a great site walked through stey by step how to incorporate handlebars template in rails](https://blog.botreetechnologies.com/using-handlebars-js-with-ruby-on-rails-bcddce004947
)

**ready to load**

Buttons were not responding when clicked if the page is redirected from other pages, instead of using the ready function, use below instead:

```
$(document).on('turbolinks:load', function(){

  	// any javascripts

});
```
