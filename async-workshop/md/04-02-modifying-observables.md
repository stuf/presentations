## Modifying Observables

Derived data

<small>Or _dependent computations_</small>

note:

- This is all neat and dandy, but how can I turn observable `a` into `b`?
- We'll look into how to derive data from existing data

v-v-v

## A misnomer

Observables can't be modified

Derive data into new Observables

[chart]

note:

- a misnomer

v-v-v

## Deriving data

`map` is your friend

You might be familiar with these

`listOfThings.map(someFunction)`

`this.props.items.map(x => ...)`

note:

- map is the go-to function to use
- specifies a mapping between the original values and new values
- for every value in the original one, apply function `f`, to get a new value
- map creates a new observable emitting all the values the original does, but with the function applied on its value

v-v-v

## Deriving Data

`map` works identical with Observables

`obs.map(someFunction)`

For every value* in `obs`, apply `someFunction`

<small>* every existing and future value</small>

Results in a new, separate Observable

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

## Great Power

`map` alone gives us great power

We can modify data into new data

We can pass that modified data somewhere else

Updated whenever original data updates

note:

- this alone enables us to do great things

v-v-v

## Not just values

Errors can be mapped, too

Values and errors coexist in Observables

`map` for values

`mapErrors` for errors

`obs.mapErrors(oldErr => newErr)`
