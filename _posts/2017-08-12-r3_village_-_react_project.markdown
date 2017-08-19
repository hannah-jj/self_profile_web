---
layout: post
title:  "R3 Village - React Project"
date:   2017-08-12 10:09:22 +0000
---


It's been many months since I started at Flatiron.  One of my dreams was to gain the knowledge to create games for kids (without any ads). Through this final project, I have realized this dream! Though the games are not at all fancy, but it's a first step in a long journey.  Here is how it all came together:

**Goal**

To teach kids about Reduce, Reuse & Recycle (R3) through games and learnings.  R3 Village is a virtual village where each villager have the options of getting new toy, replaying with old toy, recycling toy, trashing toy or learning thrugh a game without any toy.   Each action increases the pollution of the village and/or the happiness level of the villager.  Once the pollution level of the village reaches a certain level, background will go to total black.

No one can truly wins the game because pollution level increases anytime anyone get a new toy. Villagers can only survive in the long term if everyone takes part in R3 - Reduce, Reuse & Recycle. Rich or poor, when the home is destroyed, everyone is doomed.

**Plan & Action**

1. *Back-End: Rails API*

    ```
    User: has a room with 9 boxes where each box can store 1 or 0 toy
    
    Box: a box contains a toy. If the toy is recycled or trashed, box deactivated and won't show up in user's room
    
    Toy: has a name & link to where picture is stored
    
    Ingredients: various items such as plastic, electronic waste, trash, food trash to be used in recyle game
    ```
		
2. *Front-End: React*

	```
    Routes: 
	 User - index, show, new
	 Games - 3 game route. one for each of the R action

    Containers - container for each of the six routes

    Components - presentational only, create as needed to support the display in containers
	```	 

3. *The Middle - How React meets Rails*
     
    State is managed through Redux.
		 
    Containers read/write data to the database through dispatch actions passed in from the props.
    
    Each action fetches information from API server with various methods such as GET, POST & PATCH.  
    
    The response is captured by the reducers and passed back to the components as props.
    
    
		 
**Celebration**

Catch up on sleep : 

![sleep](https://media.giphy.com/media/l3M7smiKhkOcw/giphy.gif)

**Future Plan**

1. add better than primitive css
2. add more games
3. navigation

for now here is the link to the project - [https://github.com/hannah11361/R3-Village](https://github.com/hannah11361/R3-Village)

In case you haven't noticed, R3 also stands for Rails, React & Redux:

![Thank you!](https://media.giphy.com/media/3oEduJnper1UdNqreg/giphy.gif)
     


    

		
