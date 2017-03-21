---
title: CSS Animation
categories:
- css
date: 2017-03-21
---
## 1. Animation
### 1.1 Advantage
1. They're easy to use for simple animation.
2. The animation run well, even under moderate system load.
3. Browser will optimize performance and efficiency.

### 1.2 Configuring the animation
#### 1.2.1 Properties:
|name|value range|description
|:---|:---|:---
|animation-delay|`<time>`,e.g:2s|Specifies when the animation start.The value is the offset time from the time at which the animation is applied to the element.
|animation-direction|normal;reverse;alternate;alternate-reverse|Indicates whether the animation should play in reverse on alternate cycles.
|animation-duration|`<time>`,eg:3s|Configures the length of time that an animation should take to complish one cycle.
|animation-iterate-count|`<number>`,e.g:2,or infinite|Configures the number of times an animation should repeat.
|animation-name|name of @keyframes|Specifies the name of the @keyframes at-rule descripting the animation's keyframes.
|animation-play-state|runing;pause|Lets you pause and resume the animation sequence.
|animation-timing-function|ease,ease-in,ease-out,ease-in-out,linear,step-start,step-end,cubic-bezier,steps.[click here for more detail ](https://developer.mozilla.org/en-US/docs/Web/CSS/single-transition-timing-function),[tool for cubic-bezier](http://www.css3beziercurve.net/)|Configures the timing of the animation
|animation-fill-mode|none,forwards,backwards,both|Configures what values are applied by the animation before and after it is executing.
#### 1.2.2 Keyframes
##### e.g:
    p {
      animation-name: slidein;
      animation-duration: 3s;
    }
    @keyframes {
      from {
        margin-left: 100%;
        width: 300%;
      }
      75% {
        margin-left:50%;
        width: 200%;
      }
      to {
        margin-left: 0%;
        width: 100%;
      }
    }
#### 1.2.3 Using animation shorthand
Rule:The first value that can be parsed as a `<time>` is assigned to `animation-duration`, and the second one is assigned to `animation-delay`.`animation-name` can be distinguished from other properties.
##### e.g:
    // duration | timing-function | delay | interation-count | direction | fill-mode | play-state | name
    animation: 3s ease-in 1s 2 reverse both paused sliedin;
    // duration | timing-function | delay | name
    animation: 3s ease-in 2s sliedin;
    // duration | name
    animation: 3s sliedin;

#### 1.2.4 Setting multiple animation property values
The CSS animation longhand values can accept multiple values,separated by commas.
##### e.g:
    animation-name: fadeInOut, moveLeft300px, bounce;
    animation-duration: 3s, 2s;
#### 1.2.5 Using animation events
* animationstart
* animationend
* animationiteration
## 2. Run animation again
### e.g:  
#### html
      <p class="data ani">this data has animation</p>
      <button onclick=play()>play</button>
#### css
      .ani {
        animation-name: slidein;
        animation-duration: 2s;
        animation-iterate-count: 2;
      }
      @keyframes slidein {
        from {
            margin-left: 100%;
            width: 300%;
        }
        to {
          margin-left: 0%;
          width: 100%;
        }
      }
#### javascript
      function play(){
        document.querySelector(".data").className = "data";
        window.requestAnimationFrame((time)=>{
          window.requestAnimationFrame((time)=>{
            document.querySelector(".data").className = "data ani";
            });
          });
      }
## References
1. [Animaiton basic](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations#Using_animation_shorthand).
2. [single-transition-timing-function--Cubic bezier](https://developer.mozilla.org/en-US/docs/Web/CSS/single-transition-timing-function).
3. [Animation tips](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Tips).
