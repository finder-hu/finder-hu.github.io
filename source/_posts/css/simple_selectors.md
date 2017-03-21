---
title: CSS Simple Selectors
categories:
- css
- simple selectors
date: 2017-03-21
---

* Type selectors
      /*html*/
      <p>this is a p</p>
      /*css*/
      p {
        color:red;
      }
* Class selectors
      /*html*/
      <p class = "first second">this is a p</p>
      /*css*/
      .first {
      border-left: 12px solid #8F77B5;
      }
* ID selectors
      /*html*/
      <p id="thisID">this is a p</p>
      /*css*/
      #id {
        font-family: monospace;
        text-transform: uppercase;
      }
* universal selector
      /*css*/
      * {
        color: green;
      }
