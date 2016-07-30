# Virtual DOM

The Document Object Model (DOM) [1] is a tree-based representation of an HTML document that provides some methods to manipulate, access and listen to changes of (part of) the document.  

A virtual DOM is an "in memory" representation of a DOM. Since DOM operations are expensive, it is not convenient to recompute the whole DOM at every state change. For this reason, a virtual copy of the actual DOM is created. When a change occurs, a new virtual DOM is created rendering the new data state. Then a diff is calculated between the old virtual DOM and the new one and only a this point the actual DOM is patched with the diff.

## Incremental DOM

A similar but different approach is used by Incremental DOM [3]. Incremental DOM keeps only one virtual DOM and calculates diffs between the actual DOM and the virtual one. In this way memory usage is lower and, as a side effect, rendering is sometimes faster.

## Differences with the Shadow DOM

Shadow DOM [2] is a W3C spec that provides better encapsulation and compositionality for DOM. Hence, it is not related at all with Virtual DOM.

## Where we find virtual DOM

* [react](https://facebook.github.io/react/), where the idea of Virtual DOM was used for the first time.
* [virtual-dom](https://github.com/Matt-Esch/virtual-dom), low level library based in React original algorithm.
* [mithril](http://mithril.js.org/)
* [deku](https://github.com/anthonyshort/deku)
* [riotjs](http://riotjs.com/)
* [maquettejs](http://maquettejs.org/)
* [inferno](https://github.com/trueadm/inferno)
* [citojs](https://github.com/joelrich/citojs)
* [elm](http://elm-lang.org/blog/blazing-fast-html)
* [Incremental DOM](http://google.github.io/incremental-dom/#about)


## References

[1] [Document Object Model (DOM)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

[2] [Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Shadow_DOM)

[3] [Incremental DOM](http://google.github.io/incremental-dom/#about)
