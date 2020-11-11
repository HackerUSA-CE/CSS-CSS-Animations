# CSS Animations

## Intro

Learning Objectives
- students will be able to explain why animations are useful on a web sites
- students will be able to differentiate between a transform, transition and animation
- student will be able to explain what is tweening
- students will be able to apply some rules to see animations in effect
- students will be able to apply multiple rules to one element
- students will learn to make an animation using `@keyframes`

CSS animations are a simple and great way to make a web site stand out. They can draw the eye to certain elements and add engagement.

What are some common animations we see when we visit different web sites?
- slower transitions
- hamburger menus
- shaking buttons

There are three types of 'animations' available to us in css
- transform - this changes our element immediately, so we only see the end state
- transition, this allows us to set the beginning and ending state. CSS will work on the tweening (the in between states)
- animation, this allows the user to set the beginning, ending and more steps in the middle

## Get ready to code along
- navigate to your lessons folder on your computer
- `git clone xxxx`
-  `cd xxxxx`
- open the index.html and css files in your text editor - recommended split screen
- open the index.html file in your browser
- should look like xxxxx

## Our Starter code
We have two files
- `index.html` which has
  - a div with a class conainer,
  - a div for our 3 demos
- `main.css`
 - is already linked to our `index.html`
 - has some css, specific to being able to see our three demo sections more clearly and some starter elements to animate


## transform
 - HTML employs a box model, with boxes stacked on top of each other or next to each other. Typically, these boxes push and move each other out of each other's way.
 - sometimes we need to move out of this box model to add interest to our page
 - in our demo, we'll use transform to hide some text
 - we will see that animations move our animated element outside of the natural flow


 ```CSS
 .transform-demo > div {
   height: 40px;
   background: salmon;
   width: 20%;
   margin-auto;
   display: inline-block;
 }
 ```

 Right now we see a salmon colored div, we want to transform this div so that it moves to cover the text `hide me`. By providing one argument, we are going to translate the position of our salmon bar on the x-axis.

 ```CSS
 .transform-demo > div {
   height: 40px;
   background: salmon;
   width: 20%;
   margin-auto;
   display: inline-block;
   transform: translate(150px);
 }
 ```
Let's confirm our `h3` tag and it's code is still there

 ```CSS
 .transform-demo > div {
   height: 40px;
   background: salmon;
   width: 20%;
   margin-auto;
   display: inline-block;
   transform: translate(150px);
   opacity: .5;
 }
 ```

 Final question, can our salmon bar escape the container? Let's test it!

 ```CSS
 .transform-demo > div {
   height: 40px;
   background: salmon;
   width: 20%;
   margin-auto;
   display: inline-block;
   transform: translate(150px, -100px);
 }
 ```

 By adding a second argument, we have set the y  coordinates, and indeed our salmon bar can escape the confines of its parent container. And it actually goes above the the browser view! Yikes! When adjusting margins, be mindful that margins can push elements outside the bounds of the browser view.

**Bonus**: Can you figure out how to move the salmon bar just on the Y axis?

 ## Transition
 change black/white to color
 scale

In our transition demo, we have two images that are grayscale. When we hover with our mouse, the image quickly turns into color.

Let's slow down the transition by adding a role to the start state

```CSS
.transition-demo img {
  width: 200px;
  height: 200px;
  filter: grayscale(100%);
  transition-duration: 2s;
}
```

We can also add a second rule and we can add multiple effects to this rule. This demo is a bit OTT (over the top), to demonstrate the transition. However, when building web sites, be sure to use sparing and subtle animations.

```css
.transition-demo img:hover {
  filter: none;
  transform: scale(1.25) rotate(360deg);
}
```

 ## Animations

Animations allow for us to choose more steps in between the beginning and the end.

In our element to be animated, we define things about our animation
- the name of the animation
- the duration
- the delay
- the iteration count

Then we write our animation using the `@keyframes` at rule, we write rules specific to our animation

Let's make a countdown bar that shrinks and changes color.


First, let's connect our element to our `@keyframes` rule and set an `animation-duration`:

```CSS
.bar {
  border: 1px solid black;
  height: 50px;
  width: 500px;
  margin: auto;
  background-color: palegreen;
  animation-name: sale-bar;
  animation-duration: 2s;
}
```
Ah! Once our animation finishes it snaps back to it's original state. Let's add a rule to keep it's final state

```CSS
.bar {
  border: 1px solid black;
  height: 50px;
  width: 25px;
  margin: auto;
  background-color: crimson;
  animation-name: sale-bar;
  animation-duration: 2s;
  animation-fill-mode: forwards;
}
```
Our animation starts too soon! We'd like the user to have some time to see our webpage before sending them into a sale panic! Let's delay our animation for 5s.

```CSS
.bar {
  border: 1px solid black;
  height: 50px;
  width: 25px;
  margin: auto;
  background-color: crimson;
  animation-name: sale-bar;
  animation-duration: 2s;
  animation-delay: 5s;
  animation-fill-mode: forwards;
}
```

Let's add some more states, right now our transition goes from green to brown to red. let's add some yellow and orange

```CSS
@keyframes sale-bar {
  0%   {background-color: lightgreen; width: 450px}
  25%  {background-color: gold; width: 375px}
  50%  {background-color: salmon; width: 250px}
  75%  {background-color: #FF033E; width: 125x}
  100% {background-color: crimson; width: 10px}
}
```

Let's also change the very end to make this bar circular and shrink off the page

@keyframes sale-bar {
  0%   {background-color: lightgreen; width: 450px}
  25%  {background-color: gold; width: 375px}
  50%  {background-color: salmon; width: 250px}
  75%  {background-color: #FF033E; width: 125x; border-radius: 0; transform: scale(1);}
  100% {background-color: crimson; width: 10px; border-radius: 100%; transform: scale(0)}
}
