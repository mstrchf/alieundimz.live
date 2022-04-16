---
title: A look into some of the major features of React
date: 2022-04-15T09:00:00Z
tags:
  - react.js
categories: life
keywords: 
---



If you have been in the frontend scene of web development for the past 5 years or more, you have at least at some point came across React. Over the years, it has been one of the most loved front-end frameworks if not the most loved. It has contenders like Vue and Angular and recently, Svelte, which has been gaining quite the traction lately.
<br/>
In this article, I am going to talk about some of the major features that React has to provide. These features may be the reason to convince you to start using it if you haven’t already.
<br />
<br/>

- VirtualDOM
- Server-side rendering
- Reusable UI components
- Unidirectional data flow
  <br>

## VirtualDOM
  According to the React website: 
  The virtual DOM (VDOM) is a programming concept where an ideal, or “virtual”, representation of a UI is kept in memory and synced with the “real” DOM by a library such as ReactDOM.

  You probably heard already that the original DOM is slow. But how slow? What is Virtual DOM anyways? Let me answer these questions one at a time.

  First, what is “the DOM is slow”? The DOM itself is not slow. It is represented as a tree data structure. Very efficient ways have been developed to traverse through and update such data structure. It is the re-rendering that is slow. The process of painting element nodes from the DOM tree and their corresponding stylesheet take quiet the time.
### So what is the virtual DOM?
  Think of it this way, for every DOM object, there is a corresponding virtual DOM object. This new object has the same properties as the original DOM object. But since the name “virtual”, it has no means of directly changing what is shown on the screen.

  So, any modifications on the virtual DOM doesn’t cause anything to be shown on the screen.

## Server-side rendering
  When I first started learning React, I often see it mentioned everywhere that “your React application might not be very SEO friendly”. This is due to the way your application is loaded in the browser.

  When you open a React application, its HTML is served with a large JavaScript bundle. This bundle is key for your application. The issue with this is that, Search Engines will find it harder to be able to handle the JavaScript bundle properly.

  With server side rendering, you are able to serve up a fully rendered HTML to a browser. Anytime your site is visited, the server would prepare the response such that all the necessary components have been rendered into an HTML. This is then sent back as a response. Most of the time, the JavaScript sent along, is not crucial in the initial rendering process.
## Reusable UI components 
  It is crucial that when building a complex UI, you divide it into chunks. In React, this chunks are called components. They are a block of reusable JavaScript code that ultimately return HTML.

  In React, any function that returns HTML, can be looked at as a component. Since they are functions, there comes the possible of passing arguments when called. React defines a certain way of passing data to components, this is called <b>props</b>.
## Unidirectional data flow 
  As the title suggests, it is a one-way data flow where data can only be passed on in one direction to multiple parts of your application. React facilitates this with the use of <b>props</b>.

  Data that is available in one component can be passed on to another component, <b>a child component</b>, through props. This data, made available through props can only be passed from parent to child, not the other way round.
  <br/>
  There is a term referred to as <b>prop drilling</b>. This is when props are being passed around to components that do not need it but crucial to get to the intended components.</b>

  These are some of the main features of React. Be sure to check at [the official React website](https://reactjs.org) for more information. Adios!
