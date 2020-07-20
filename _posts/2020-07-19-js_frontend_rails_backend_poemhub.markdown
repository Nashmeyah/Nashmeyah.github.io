---
layout: post
title:      "JS FrontEnd/ Rails Backend PoemHub"
date:       2020-07-20 02:12:47 +0000
permalink:  js_frontend_rails_backend_poemhub
---


I have studied Javascript in college, it wasn’t that intimidating then, i actually had quite alot of fun learning it and using it for front end development. When we started learning JS, I had some confidence in learning the material because i was already exposed to it before… I did not expect us to go so far and so quickly despite the fact the pace we did with Ruby. Only the first two days was a review for me of everything i learned in college and i didnt realize how much i actually didnt know of JS. 
 
 
For my project, I decided to keep it simple to really prove my understanding of Javascript in the front end and incorporating the Rails background. I built a simple Poem hub for poets to post their poems on the page. I used a fetch request from my backend database yo display all the poems for that poet. The poet is able to add and delete the poems belonging to the poets.
 
 
I also added a class to initialize the poems for the poets when created. Building this app was definitely a challenge. I couldnt wrap my head around JS so easily, all in all I liked that I was able to test all my skills and study the parts that werent so clear to me. 
 
 
This part of code,
```
let poem = new Poem(data);
      poem.renderPoem();
```
Reminded me of ruby when we initialize our objects. This part was very easy to understand because of its similarity.  
Something that I found very interesting is that javascript functions can still talk to each other through different files, This is very intriguing because it allows you to keep your information very organized and less JS clutter. 
 
 
 
```
class Poem {
  constructor(data) {
    this.id = data.id;
    this.poet = data.poet;
    this.title = data.title;
    this.body = data.body;
  }
 
  renderPoem() {
    let card = document.querySelector(`[data-id='${this.poet.id}']`);
    let ul = card.querySelector(".poems-list");
 
    let poemCard = document.createElement("li");
    poemCard.id = `poem-${this.id}`;
    poemCard.innerText = `Title: ${this.title}`;
    let releaseBtn = document.createElement("button");
    releaseBtn.className = "delete";
    releaseBtn.dataset.poemId = this.id;
    releaseBtn.innerText = "Delete";
    releaseBtn.addEventListener("click", deletePoem);
    ul.appendChild(poemCard);
    poemCard.appendChild(releaseBtn);
  }
}
```
 
 
This class is in its own js file, the js file has a specific role and allows me to understand what each piece is doing and less confusion as well as easier to spot bugs and errors. 

 
 

