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

v-v-v

## Observing Observables 1/2

_All Observables_ have an `observe` method

_Main method_ for making Observables work with the world

```js
simpleValue.observe(value => {
  console.log('I got a value!', value);
});
```

note:

- later on stuff about activation and deactivation
- important thing to know is without `observe` somewhere down the line, the Observable does nothing
- `observe` returns undefined, so it's best to keep `observe` separate from the chain
- keep all side-effects in `observe` calls — like using the value to set a button's text

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

### Exercise time

Open `exercise-basics.js`

Fill the missing gaps

v-v-v

## Observables are a box

Observables are containers

You can put stuff in it (value)

You can move the box around (pass it along)

Easier to move stuff around in a box

[box picture]

note:

- helps to get an overview, not the most accurate thing tho
- imagine observables are a box that you can put values into
- it's great for storing stuff, but comes with compromises
- boxes are great to transport stuff in; imagine moving to a new apartment and not having boxes for your stuff, it's horrible
- but boxes have their drawbacks

v-v-v

Now, imagine you have two boxes of stuff

You want to add them together

`+` does not work, you can't put two boxes together like that, what are you doing

You need to open the boxes up and decide on some way to combine them together

note:

- you can't poke a box' content without first opening it up (lift, map)
- you can't plus two boxes together to end up with one big box with both boxes contents
- you'll have to open the boxes up and decide how you combine the contents
- but what about errors

v-v-v

note:

- errors can be transported in the box along with the rest of your stuff
- you can choose to ignore errors, or values, or maybe even both, depending on the situation
- but it might be beneficial to handle errors in some way
- operations work on just one value
- metaphor time: (next slide)

v-v-v

note:

- on errors
- imagine you're moving to another apartment, you have a cat
- your cat is stressed out, it doesn't know what to do (bad network connection to REST API)
- the cat uses your box as a litter box, now you have shit along your stuff
- you don't have to do anything about it, you can transport the box just fine without anything about it
- but sooner or later you might want to do someting about it, or your stuff will smell like shit

v-v-v

note:

- values into errors, and the other way
- value.flatMapLatest(x => constantError(x)) (value -> error)
- value.flatMapErrors(x => constant(x)); (error -> value)

v-v-v

|          | Single     | Multiple     |
|----------|------------|--------------|
| **Pull** | `Function` | `Iterator`   |
| **Push** | `Promise`  | `Observable` |

note:

- pull and push are concepts brought up on the thought of how data is propagated to some section (described in next slide)
- regular data is pull, while reactive/future data is push

v-v-v

|          | Producer | Consumer |
|----------|----------|----------|
| **Pull** | **Passive**<br><small>produces data when requested</small> | **Active**<br><small>decides when data is requested</small> |
| **Push** | **Active**<br><small>produces data at its own pace</small> | **Passive**<br><small>reacts to received data</small>       |

note:

- the contrast between the two is simply in which who is passive and who is active
- `pull` data requires us to manually "pull" the data _when_ we need it
- `push` allows us to passively _observe_ data, without needing to think _when_

v-v-v


