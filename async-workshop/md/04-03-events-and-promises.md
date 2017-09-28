## Events and Promises

v-v-v

`Kefir.fromEvents(document, 'click')`

`Kefir.fromPromise(fetch('https://...'))`

v-v-v

`Kefir.fromEvents(document, 'click')`

Creates an Observable out of an event subscription

Emitted values will be events just like in an event listener

```js
Kefir.fromEvents(document, 'click')
     .observe(event => ...)
```

is equivalent to

```js
document.addEventListener('click', event => ...);
```

v-v-v

`Kefir.fromPromise(fetch('https://...'))`

Creates an Observable out of a Promise

Emits a value if Promise is resolved, error is rejected

```js
Kefir.fromPromise(fetch('https://...'))
     .observe(response => ...)
```

is equivalent to

```js
fetch('https://').then(response => ...)
```

v-v-v

## But you're not thinking in Observables

You can specify what you want to do with events

```js
Kefir.fromEvents(document, 'click')
     .map(event => event.target)
     .debounce(250)
     .observe(...) // <= will receive only event target, debounced 250 ms apart
```

v-v-v

### Exercise

Open `exercise-events-and-promises.js`

Fill `undefined` values
