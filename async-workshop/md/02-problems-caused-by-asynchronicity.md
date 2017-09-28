## Problems caused by asynchronicity

<p class="framgent">
Introduces the notion of _time_
</p><!-- .element: class="fragment" -->

Does not fit well with imperative code <!-- .element: class="fragment" -->

<small>Although there are some helpers in this</small> <!-- .element: class="fragment" -->

Dealing with data you might not have yet <!-- .element: class="fragment" -->

Blocking vs non-blocking, concurrent <!-- .element: class="fragment" -->

note:

- additional things to consider
- async introduces the notion of time
- ES specs now have async/await
- if you know functors, things will be easy

---

## The notion of time

Normally, we don't have to care<!-- .element: class="fragment" -->

```js
const x = 10;
const y = 20;
const z = x + y; // => 30
```
<!-- .element: class="fragment" -->

But what if the we have this? <!-- .element: class="fragment" -->

```js
const x = Kefir.later(1000, 10);
const y = Kefir.later(500, 20);
const z = x + y; // => [later][later]
// you are lying to me wtf
```
<!-- .element: class="fragment" -->

---

<img src="img/cat-needs-assistance.jpg">

---

## Does not fit well with imperative code

<p>
ES7 introduces `async` and `await` keywords
</p> <!-- .element: class="fragment" -->

Uses Promises under the hood <!-- .element: class="fragment" -->

Works nicely-ish with imperative code <!-- .element: class="fragment" -->

Might give illusion not to learn Promises, leading to confusion <!-- .element: class="fragment" -->

---

## Blocking vs non-blocking

<div class="cols">
  <div class="fragment">
    <pre><code data-trim data-noescape class="lang-js hljs javascript"><span class="hljs-keyword">for</span> (i = <span class="hljs-number">0</span>; i &lt; <span class="hljs-number">100000</span>; i++) {
  fs.readFileSync(<span class="hljs-string">'bigfile'</span>);
}
    </code></pre>
  </div>
  <div class="fragment">
    <pre><code data-trim data-noescape class="lang-js hljs javascript"><span class="hljs-keyword">for</span> (i = <span class="hljs-number">0</span>; i &lt; <span class="hljs-number">100000</span>; i++) {
  fs.readFile(<span class="hljs-string">'bigfile'</span>);
}
    </code></pre>
  </div>
</div>

Which do you think is faster? <!-- .element: class="fragment" -->
