## Modifying Observables

Derived data <!-- .element: class="fragment" -->

<small>Or _dependent computations_</small> <!-- .element: class="fragment" -->

note:

- This is all neat and dandy, but how can I turn observable `a` into `b`?
- We'll look into how to derive data from existing data

v-v-v

## A misnomer

Observables can't be modified <!-- .element: class="fragment" -->

Derive data into new Observables <!-- .element: class="fragment" -->

[chart]

note:

- a misnomer

v-v-v

## Deriving data

<p>`map` is your friend</p> <!-- .element: class="fragment" -->

You might be familiar with these <!-- .element: class="fragment" -->

`listOfThings.map(someFunction)` <!-- .element: class="fragment" -->

`this.props.items.map(x => ...)` <!-- .element: class="fragment" -->

note:

- map is the go-to function to use
- specifies a mapping between the original values and new values
- for every value in the original one, apply function `f`, to get a new value
- map creates a new observable emitting all the values the original does, but with the function applied on its value

v-v-v

## Deriving Data

<p>`map` works the same way here</p> <!-- .element: class="fragment" -->

`obs.map(someFunction)` <!-- .element: class="fragment" -->

<p>For every value* in `obs`, apply `someFunction`</p> <!-- .element: class="fragment" -->

<small>* every existing and future value</small> <!-- .element: class="fragment" -->

Results in a new, separate Observable <!-- .element: class="fragment" -->

note:

- when I say every value in `obs`, I mean _every_ value
- can be used to create separate, simple and specific observables

v-v-v

## Example

Let's imagine `tick` gives a `Date` object every second

```js
// The long date with time -string
const timestampAsString = tick.map(value => value.toString());

// Just the time
const timeAsString = tick.map(value => value.toTimeString());

// Just the date
const dateAsString = tick.map(value => value.toDateString());
```

Now we have three new Observables

Will be updated whenever `tick` is updated

note:

- this is the major point that might take time to "get"
- `Array.map` applies a function on every value it gets
- `Observable.map` applies a function on every value it gets

v-v-v

## Useful

<p>`map` alone gives us great power</p> <!-- .element: class="fragment" -->

We can modify data into new data <!-- .element: class="fragment" -->

We can pass that modified data somewhere else <!-- .element: class="fragment" -->

Updated whenever original data updates <!-- .element: class="fragment" -->

note:

- this alone enables us to do great things
- we can create new data without much effort
- because observables are lazy, we only use as the resources we need

v-v-v

## Not just values

Errors can be mapped, too <!-- .element: class="fragment" -->

Values and errors coexist in Observables <!-- .element: class="fragment" -->

<p>`map` for values</p> <!-- .element: class="fragment" -->

<p>`mapErrors` for errors</p> <!-- .element: class="fragment" -->

<p>`obs.mapErrors(oldErr => newErr)`</p> <!-- .element: class="fragment" -->

note:

- errors go in parallel with values
- errors and values have both separate operations
- `map` does not work on errors
- `mapErrors` does not work on values

---

### Exercise

Open `exercise-mapping.js`

Fill `undefined` values

---

## Modifying Observables, part 2

<p>`map` is just one of many</p> <!-- .element: class="fragment" -->

<p>`filter`, `scan`, `debounce`</p> <!-- .element: class="fragment" -->

<p>`take`, `takeWhile`, `takeErrors`</p> <!-- .element: class="fragment" -->

<p>`skip`, `skipWhile`, `skipErrors`</p> <!-- .element: class="fragment" -->

v-v-v

## Exercise

Open `exercise-after-map.js`

Fill `undefined` values
