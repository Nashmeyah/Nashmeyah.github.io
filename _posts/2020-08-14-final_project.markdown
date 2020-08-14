---
layout: post
title:      "Final project"
date:       2020-08-14 17:05:39 +0000
permalink:  final_project
---

My final project for the bootcamp is a rails api backend with a rails and redux frontend. For the project, I decided to build something simple for now, but still allow me to grow on the project and add complexity to it( I mean technically you can do that with anything, but you know what I mean). I created a StoryCreation app, it allows you to create draft stories almost like jotting down ideas, or an idea you want to build on. It allows you to create characters and I will eventually add the feature to be able to update each character as desired. 

	The most complicated part of this development that I learned from was the redux fetch actions. The relationship when it comes to redux is  Action -> Reducer -> Updated State. 

When you create an action for a fetch request, in the second .then, you send a dispatch to reduce this action so that it updates the state. 

```
export const getStories = () => {
  return (dispatch) => {
    dispatch({ type: "LOADING_STORIES" });
    fetch("/stories")
      .then((response) => response.json())
      .then((stories) =>
        dispatch({ type: "STORIES_LOADED", payload: stories })
      );
  };
};
```
Here is an example for a GET request, I sent a request to my backend API to fetch all the stories, and then i sent the dispatch action to update my store that way i will be able to access this information all throughout my app. I am able to do this using the { connect } that comes from react-redux library. 

	The most pleasing part of this app is when i created my hooks. In my form component, I had internal state to capture the data, then send it off to my store. I created a functional component because the purpose of this was to have one job only, and that is capture the data from the form, place it in the internal state, then send it off to my store. 
	
```
 const [title, setTitle] = useState("");
 
  const [body, setBody] = useState("");
```

My Interal state looks like this, and I am abe to use the useState from react library, 

```
const handleSubmit = (event) => {
    event.preventDefault();
    const story = {
      title,
      body,
    };
    props.createStory(story);
    setTitle("");
    setBody("");
  };
```
 
After capturing the data from the user and placing it in state then sending it off… more or less this was the code to get the job done. 

	This app by far was the hardest for me to create throughout all my projects, but i learned so much from it. I learned so much here at FlatIron, and I can honestly say, I cannot wait to try more things and build more things, and learn new languages daily. 
Check out my github for access to this project if youd like to take a look at it. 
https://github.com/Nashmeyah/StoryLine

