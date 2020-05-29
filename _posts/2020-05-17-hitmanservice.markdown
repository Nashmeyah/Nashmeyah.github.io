---
layout: post
title:      "HitmanService"
date:       2020-05-17 10:08:59 -0400
permalink:  hitmanservice
---

   Sinara was pretty fun, although the ActiveRecord CRUD was hard to wrap my head around, more coding  practice with it and it will click. I liked learning about the RESTful routing, How the internet works with HTTP requests is fascinating. HTTP defines a set of request methods to indicate the desired action to be performed for a given resource, they are also referrred to as HTTP verbs, you can read about them in detail here -> https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
	 
*            GET        /victims     index
* 					 
* 					 GET        /victims/new    displays form to create new victim
* 					 
* 					 POST     /victims     creates new victim and saves to the database
* 					 
* 					 GET        /victims/:id    shows the current victim
* 					 
* 					 GET         /victims/:id/edit   displays form to edit selected victim
* 					 
* 					 PATCH    /victims/:id    edits the selected victim and saves to the database
* 					 
* 					 DELETE    /victims/:id   deletes victim from the database
	 
	 These are the basic ActiveRecord CRUD (create, read, update, destroy/delete) actions I used to build my app, that allow for http requests to be made and sent back with information. In order for the correct, and the specific information the user asked for correctly, this allows cookies and sessions to come into play so that the browser remembers a specific user and remembers who is making a request. 
	
	 For example, when you log into facbook, and you click between links and the reason you dont need to login in each time you go to another page, thats because the cookie in your brower has what is called a session that stores a user_id with your specific id and remembers you each time you log also stays remembering you unless you sign out. The reason this happens is because when Tim Berners-Lee created HTTP(Hypertext-transfer-protocol) and HTML in 1989, he created it to be stateless. That means each request made in the browser is made independently therefore the browser forgets the previous request that was sent.

		With that being said, the curriculum I have learned in the past 3 weeks has allowed me to have successfuly complete a killer app. Literally... For my Sinatra project I wanted to build something that I would have fun with and that I would learn from rather than just get the project done. I decided to build an app for a killer to keep track of its victims. The reason why I chose to build those based off Killer and Victim is to put it simply I really like playing video games, such as thriller and action games and I also love crime stories whatever form they come in. 
		This app allows killers to create an account and create a new victim when desired, they can add information such as name, time of death, and their finals words. My app contains 2 models, Killer and Victim.
		
		```class Killer < ActiveRecord::Base
    has_secure_password
    has_many :victims
    validates :name, :email, uniqueness: true
    validates :name, :email, presence: true
end```
		
		```class Victim < ActiveRecord::Base
    belongs_to :killer
    validates :name, :time_of_death, :last_words, presence: true
    end```
		
		Killer has_many victims. I kept the relations simple so I am able to understand how to build the app on my own and test my knowledge,  I also have future plans to build on this app and have it grow with more than just 2 models as well as add more functionality to it with the new information I will learn in the future.
