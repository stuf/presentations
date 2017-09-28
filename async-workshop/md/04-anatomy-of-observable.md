## The Anatomy of Observables

<img src="img/observable-raguchans.jpg">

<small>Picture of two Observables containing cats</small>

v-v-v

## Getting started

We'll start with some exercises soon

Clone the git repo `github.com/stuf/async-workshop` <!-- .element: class="github" -->

Exercises are located in the `public` folder <!-- .element: class="github" -->

v-v-v

## Observables

Essentially containers for data <!-- .element: class="fragment" -->

They have a lifecycle <!-- .element: class="fragment" -->

<p>
`value`, `error` and `end`
</p> <!-- .element: class="fragment" -->

note:

- observables have a life of their own
- they don't emit anything on start
- they emit either a `value`, an `error`, or that they've `end`ed

v-v-v

## In pictures

```
|----(1)----(2)----(3)----e----X

            | = start
(1), (2), (3) = values
            e = error
            X = end
```

note:

- easier to understand if we think of observables like this
- they start, we don't have to care about it
- they may emit `value`s or `error`s
- they may or may not `end`
- `end`ing and observable means if we end up emitting values from it, they will get ignored

v-v-v

## Creating simple Observables

<p>`Kefir.constant(123)`</p> <!-- .element: class="fragment" -->

<small>Observable that emits a value</small> <!-- .element: class="fragment" -->

`Kefir.constantError('error message')` <!-- .element: class="fragment" -->

<small>Observable that emits an error</small> <!-- .element: class="fragment" -->

`Kefir.never('foo')` <!-- .element: class="fragment" -->

<small>Observable that has already ended</small> <!-- .element: class="fragment" -->

`Kefir.later(1000, 'I\'m late')` <!-- .element: class="fragment" -->

<small>Observable that emits a value later</small> <!-- .element: class="fragment" -->

note:

- most of these are fairly explanatory, but what about `never`?
- it doesn't seem very useful
- we'll go through it later on, but it has its uses
- next slide is a little dense, don't be scared, there won't be many of these

v-v-v

## Observing Observables 1/2

<p>_All Observables_ have functions for observing</p> <!-- .element: class="fragment" -->

The only function you can use to interact with the outside world <!-- .element: class="fragment" -->

<p>There exist `onValue`, `onError` and `onEnd` functions</p> <!-- .element: class="fragment" -->

```js
simpleValue.onValue(value => console.log('I got a value!', value));

simpleValue.onError(err => console.error('Something broke :('));

simpleValue.onEnd(() => console.info('Stream ended'));

simpleValue.observe(onValue, onError, onEnd);
```
 <!-- .element: class="fragment" -->

note:

- later on stuff about activation and deactivation
- important thing to know is without `observe` somewhere down the line, the Observable does nothing
- `observe` returns undefined, so it's best to keep `observe` separate from the chain
- keep all side-effects in `observe` calls — like using the value to set a button's text
- `obs.observe(fn)` is identical to `obs.onValue(fn)`
- `obs.observe(fn1, fn2, fn3)` calls `fn1` on value, `fn2` on error, `fn3` on end
- may feel overwhelming, but this is probably the most complex stuff you'll have

v-v-v

## Observing Observables 2/2

<p>_All Observers_ also have a `log` method</p> <!-- .element: class="fragment" -->

Good for debugging, prints the value in the console <!-- .element: class="fragment" -->

<p>Works as a _pass-through version_ of `observe`</p> <!-- .element: class="fragment" -->

```js
simpleValue.log('simple value');

// => simple value <value> 123

error.log('an error');

// => an error <error> "Please help me"
```
<!-- .element: class="fragment" -->

note:

- not a one-off call, every time an observable's value changes, it will be logged
- can cause a fair share of weirdness due to activation and deactivation

v-v-v

## Observables in Summary

<p>Observables emit `value`, `error` or `end`</p> <!-- .element: class="fragment" -->

<p>Observables can be `observe`d</p> <!-- .element: class="fragment" -->

<p>Observables can be `log`ged</p> <!-- .element: class="fragment" -->
