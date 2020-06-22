---
layout: post
title:      "Devise, Oauth, Admins, and ActiveRecord Associations. "
date:       2020-06-22 21:34:22 +0000
permalink:  devise_oauth_admins_and_activerecord_associations
---


For my Rails project, I initially wanted to build an app to organize and manage art classes and art projects. Now I know technically you can’t really put an art project online, but I figured that I could add assignments to the class that way a student can keep track of the requirement. As I was building the app, it slowly started to develop into a school domain, students were able to add any course they liked as well as drop any course, add projects, delete projects, view other classes and so on. When a student logs in, their dashboard allows them to view projects, view courses, and browse courses and categories. This app has two joins tables, one for users and courses for when they sign up to a course, also a joins table for userscourses and projects for students to view what project is for what course. 

I played around in the schema over a dozen times and I played in the rails console and pry so much just to wrap my head around the rails associations and joins tables. I thought I understood the has_many and ‘has_many, through:’ relationships as well as the nested routes and nested forms, but as I built my app, I had a really hard time knowing what to do next and what the extent of my relations were. The ActiveRecord ‘has_many, through:’ and belongs_to relationships were the most that tripped me up. When you create a new instance, do not forget to add accepts_nested_attributes: to your model! This allows the ability to associate the child and parent together. 

I also was able to Devise to my app, when Nancy first demonstrated the ability of the Devise gem for us, I was intrigued immediately, I loved how much this gem saves time and the power it has to add security for your sessions and users log in and sign up actions. So much code gets created under the hood with such a simple setup. https://medium.com/@mchisti/creating-simple-users-in-rails-with-devise-gem-tutorial-cd91d2ef36d5 This article is a great explanation of how to get setup using Devise in your Rails app. *Side note….don't forget to get your github repo setup. *

I incorporated 3rd party sign in/signup using the omniauth gem. Learning about this gem was also a bit complicated and hard to wrap my head around. When using a 3rd party gem, there are alot of specifications to how the provider you use wants things setup. Facebook is a good example, when using it as a 3rd part auth, it can get tricky real quick. I used github, because 1. I learned how to use it in the cohort lol... and 2, it was easy. https://github.com/omniauth/omniauth  If you plan on using it, read the details very carefully to save yourself a lot of headache. 

Lastly, I incorporated an admin side to my app, so that someone on the admin side is able to create courses and categories for their students to join and create projects/assignments for. Developing the app took a lot longer and a lot harder than our previous projects, but I am glad I was able to see it through how I wanted it to work. 

https://github.com/Nashmeyah/ArtClass --- My repo if you're interested to see my code, :) enjoy!
