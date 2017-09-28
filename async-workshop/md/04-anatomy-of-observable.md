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

Containers for data

They have a lifecycle

`value`, `error` and `end`

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

```js
// An Observable that will emit a value instantly and then end
const simpleValue = Kefir.constant(123);

// An Observable that will emit an error and then end.
const error = Kefir.constantError('Please help me');

// An Observable that will never emit anything
const alreadyOver = Kefir.never('Nobody will ever notice me');

// An Observable that will emit a value after three seconds
const late = Kefir.later(3000, 'Sorry I\'m late');
```

note:

- most of these are fairly explanatory, but what about `never`?
- it doesn't seem very useful
- we'll go through it later on, but it has its uses
- next slide is a little dense, don't be scared, there won't be many of these

v-v-v

## Observing Observables 1/2

_All Observables_ have functions for observing

The only function you can use to interact with the outside world

There exist `onValue`, `onError` and `onEnd` functions

```js
simpleValue.onValue(value => console.log('I got a value!', value));

simpleValue.onError(err => console.error('Something broke :('));

simpleValue.onEnd(() => console.info('Stream ended'));

simpleValue.observe(onValue, onError, onEnd);
```

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

_All Observers_ also have a `log` method

Good for debugging, prints the value in the console

Works as a _pass-through version_ of `observe`

```js
simpleValue.log('simple value');

// => simple value <value> 123

error.log('an error');

// => an error <error> "Please help me"
```

note:

- not a one-off call, every time an observable's value changes, it will be logged
- can cause a fair share of weirdness due to activation and deactivation

v-v-v

## Observables in Summary

Observables emit `value`, `error` or `end`

Observables can be `observe`d

Observables can be `log`ged
