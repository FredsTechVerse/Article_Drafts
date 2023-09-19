# WHAT IS THE DIFFERENCE 

- Transitions are actions based while animations aren't but they both involve a change of css properties with the animations being more flexible .

## CSS ANIMATIONS
- With the animations , we just need to link a keyframe to an element using the animation name property.

```css 

@keyframes example {
  from {background-color: red;}
  to {background-color: yellow;}
}

@keyframes example {
  0%   {background-color: red;}
  25%  {background-color: yellow;}
  50%  {background-color: blue;}
  100% {background-color: green;}
}

/* The element to apply the animation to */
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 4s;
}
```
# CSS TRANSITIONS

- With transitions , no keyframes are involved we simply give our element a heads up on the property/properties changing and go ahead to change it on desired user action eg hover. 

```css
div {
  width: 100px;
  height: 100px;
  background: red;
  transition: width 2s;
}

div:hover {
  width: 300px;
}

```

## WHAT WAS LACKING
- The confusing bit was the css properties we wanted to change . In my portfolio astro build in animation will be sleek and sufficient enough.
- A transformation is a css property so it can be transitioned. 
- The most famous transformations are translate , rotate , scale skew and matrix. They can happen in 2D or 3D. Example 
```css 
div {
  transform: translate(50px, 100px);
}
```
