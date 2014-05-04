---
layout: post
title:  "JavaScript number array summation"
date:   2013-07-29 01:13:13
<!-- categories: jekyll update -->
---

eg.

```javascript
var array = [1,2,3,4,5];
// sum = 1 + 2 + 3 + 4 + 5 = 15;
// join array
var array_join = array.join('+'); // => "1+2+3+4+5"
// eval string
var array_sum = eval(array_join); // => 15
```

eg.

```javascript
//sum jQuery selector element values
var elements = $('input:checked')
var values = elements.map(function(){return $(this).val() - 0}).get();
var sum = eval(values.join('+'));
```