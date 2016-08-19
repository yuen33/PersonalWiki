## [原創] Something about float and clear in CSS [Back](./../post.md)

### Description

As we all know that, a `div` element is a block element, which will occupy the whole line.

<p data-height="498" data-theme-id="21735" data-slug-hash="vKrgbZ" data-default-tab="css,result" data-user="aleen42" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/aleen42/pen/vKrgbZ/">vKrgbZ</a> by aleen42 (<a href="http://codepen.io/aleen42">@aleen42</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

### Float

Normally, We'll suppose that all those `div` elements have been in a normal standard flow (標準流).

CSS have provided an attribute named `float` to allow you to design block elements into a same line. If you set `float` to a `div`, you will find that this element will get rid of the original standard flow, and as following example, you will see that `div2` has get rid of the standard flow, and `div3` has been moved uppper following behind `div1`.

<br/>

<p data-height="493" data-theme-id="21735" data-slug-hash="wWkJwQ" data-default-tab="css,result" data-user="aleen42" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/aleen42/pen/wWkJwQ/">wWkJwQ</a> by aleen42 (<a href="http://codepen.io/aleen42">@aleen42</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

<br/>

`float` attribute can be set as `left` or `right`, that means you can float this element to the left or right;