## Chaining Observables

<img src="img/catbox.jpg" style="width: 40%">

v-v-v

## Reiterating last part

`Kefir.fromPromise`

```js
Kefir.fromPromise(fetch('https://...'))
     .map(response => response.json());
```
<!-- .element: class="fragment" -->

Can you see something wrong? <!-- .element: class="fragment" -->

<small>`response.json()` returns a Promise</small> <!-- .element: class="fragment" -->

v-v-v

<p>Okay, so `fromPromise` it, too</p><!-- .element: class="fragment" -->

```js
Kefir.fromPromise(fetch('https://...'))
     .map(response => Kefir.fromPromise(response.json()))
```
<!-- .element: class="fragment" -->

But this doesn't work either <!-- .element: class="fragment" -->

Because we will get an Observable that contains an Observable <!-- .element: class="fragment" -->

v-v-v

What we want is the value, not the box <!-- .element: class="fragment" -->

```js
Kefir.fromPromise(fetch('https://...'))
     .flatMap(response => Kefir.fromPromise(response.json()))
```
<!-- .element: class="fragment" -->

This works <!-- .element: class="fragment" -->

v-v-v

<img src="img/ineedhelp.jpg" style="height: 40vh">

But how? Why?<!-- .element: class="fragment" -->

v-v-v

## Meet flatMap and family

<p>`flatMap` works like `map`</p><!-- .element: class="fragment" -->

<p>`flatMap` requires you to return an Observable</p><!-- .element: class="fragment" -->

<p>Works as a bridge from one Observable to another</p><!-- .element: class="fragment" -->

v-v-v

### Examples

```js
Kefir.constant(123)
     .flatMap(v => Kefir.constantError(v))
```
<!-- .element: class="fragment" -->

<small>Turn values into errors</small><!-- .element: class="fragment" -->

```js
Kefir.sequentially(1000, [1, 2, 3, 4, 5])
     .flatMap(v => Kefir.sequentially(500, [v, v, v, v, v]))
```
<!-- .element: class="fragment" -->

<small>Repeat every value five times</small><!-- .element: class="fragment" -->
