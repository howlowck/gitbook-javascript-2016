# Who controls Javascript?

When we say Javascript, before NodeJS, we were only talking about javascript in the browser. 

Javascript implemented in the browser is actually governed by two different standard-governing entities: [ECMA Internal group](http://www.ecma-international.org/ecma-262/5.1) and [W3C\/WHATWG](https://html.spec.whatwg.org/).

> _**Note:**_ W3C and WHATWG are actually two totally different groups with two different HTML5 specs! [See the difference](https://www.w3.org/wiki/HTML/W3C-WHATWG-Differences).

ECMA sets the standard for javascript as a language (called ECMAScript), while W3C/WHATWG defines the javascript bindings to the DOM in the browser.

This separation might seem clear on paper, it's often not obvious to people. For example, the `setTimeout` function is not an ECMA standard; it's actually a method that exists on the `WindowTimers` Object that's globally available in the browser context. Meanwhile, `parseInt` function **is** a ECMA standard.

WHATWG was born out of the stagnation of W3C when it was slow to adapt emerging best-practices.  When WHATWG's popularity increased, W3C adapted much of what WHATWG was working and now known as HTML5. [Read more on Wikipedia](https://en.wikipedia.org/wiki/WHATWG)
