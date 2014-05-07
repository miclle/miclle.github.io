---
layout: post
title:  "JavaScript 数组去重"
date:   2011-02-10 07:45:35
categories: [JavaScript]
tags: [JavaScript]
---

function unique(array){

 array.sort();

 for ( var i = 1; i   if ( array[i] === array[i-1] ) {

   array.splice(i--, 1);

  }

 }

 return array;

}