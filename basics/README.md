# Javascript Clarified

When we say Javascript, before NodeJS, we are talking about javascript in the browser.  Javascript implemented in the browser is actually governed by two different governing bodies: ECMA Internal group and W3C/WHATWG.  

> ***Note:*** W3C and WHATWG are actually two totally different groups.

ECMA sets the syntactic standard for javascript (called ECMAScript), while W3C/WHATWG defines the javascript bindings to the DOM in the browser.  While the separation is clear on paper, it's not often obvious to developers. For example, `setTimeout` function is not an ECMA standard, it's actually a method that exists on the `WindowTimers` Object that's globally available in the browser context. 
