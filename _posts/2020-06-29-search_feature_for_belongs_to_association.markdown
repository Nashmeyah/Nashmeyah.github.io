---
layout: post
title:      "Search feature for belongs_to association"
date:       2020-06-30 03:47:41 +0000
permalink:  search_feature_for_belongs_to_association
---


My MVC structure and ActiveRecord associations are: 
* Category has_many courses
* Category has_many :userscourses, through: :courses
* Courses belongs_to  :category
* Courses has_many :userscourses
* Course has_many :projects, through: :userscourses
* User has_many :userscourses
* User has_many :projects, through: :userscourses
* Userscourse belongs_to :user
* Userscourse belongs_to :course
* Userscourse has_many :projects
* Project belongs_to :userscourse
* Project belongs_to :user
 
I wanted to build a search feature in my app, but since a course belongs_to a category and i dont have a course index unless the course is associated with the category. I had to figure out a way to build this feature using what i know about ActiveRecord associations. 
 
So generally, building a search feature requires a form. The form was built using a form_tag, but you can build it using form_with and form_for. 
 
```
<p>Search Courses:</p>
            <%= form_tag(categories_path, method: :get) do%>
                <%= text_field_tag(:search, params[:search])%>
                <%= submit_tag "Search"%>
            <%end%>
            <br>
```
This sets up my search in the Categories index page. The html form that is displayed in the browser then looks like this…
 
```
<form accept-charset="UTF-8" action="/categories" method="get">
  <input id="search" name="search" type="text" />
  <input name="commit" type="submit" value="Search" data-disable-with="Search" />
</form>
 
```
 
The reason we do this in the view  is because we want to filter the results on our index page, not post anything to our database. After clicking submit, the program will reload the index view page, but this time with the search results.
 
After this is set up, We need to then prepare the index page to accept the params if provided, so we make changed to the index action in the Categories controller like this…
 
```
def index
        if params[:search]
            @course = Course.search(params[:search])
        end
        @category = Category.all
    end
```
 
We also need to add a method in out Course model, since that is what we are going to look for in the search feature. 
 
```
def self.search(search)
        if search
            where(["name LIKE ?", "%#{search}%"])
        end
    end
```
 
 
Finally, in the view, we display our results as well as add a link_to so that the user can click on the course they were searching for and redirects them successfully to the course show page.
 
```
<% if @course%>
                <% @course.each do |course| %>
                <ul>
                    <li><%= link_to course.name, category_course_path(course.category_id, course.id) %></li>
                </ul>
                <br>
            <%end%>
    <%end%>
```
 
The link I set up `category_course_path(course.category_id, course.id)` allows the redirect to successfully go the course that is associated with that category based off the search results since they change each time and vary. 
 
 

