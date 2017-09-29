## Brief history of async JS

v-v-v

### The Players

Events

Callbacks

Promises

Streams

<small>There are more, but these ones are the most relevant</small>

v-v-v

### Generally speaking

Non-blocking <!-- .element: class="fragment" -->
Parallel operations <!-- .element: class="fragment" -->

v-v-v

### Events

Supported since Netscape times <!-- .element: class="fragment" -->

Pub-sub messaging <!-- .element: class="fragment" -->

Difficult to pass result around <!-- .element: class="fragment" -->

Combining multiple results is annoying <!-- .element: class="fragment" -->

Small cost upfront, hidden costs <!-- .element: class="fragment" -->

note:

- explicit subscription, "only interested in this"
- solutions concentrate on handling the result there and then
- passing value around requires laborous solutions, like event aggregation
- this is perfectly fine for some things, but we can do better

v-v-v

### Callbacks / CPS

Node.js began using continuous-passing style (callbacks) for async <!-- .element: class="fragment" -->

Operation is given function to call when done <!-- .element: class="fragment" -->

The Callback Hell is real <!-- .element: class="fragment" -->

Difficult to pass result around <!-- .element: class="fragment" -->

Combining multiple results is annoying <!-- .element: class="fragment" -->

note:

- base concept is old (1975)
- operation takes callback function as last param to call when done
- but same problems as events
- some workarounds exist, but solutions concentrate on handling the result there and then
- not really meant for combinators etc.

v-v-v

### Promises

Introduced into JS fairly "recently" <!-- .element: class="fragment" -->

<p>_Proxy object_ for future data</p> <!-- .element: class="fragment" -->

Can be passed around like normal data <!-- .element: class="fragment" -->

Gateway drug to Streams <!-- .element: class="fragment" -->

note:

- old idea as well, studied since 1980's, concept from 1970's
- popularized as deferreds back in 2011 by jquery, among others
- can be passed around to where the result is wanted
- it's just a box for eventual data
- value and error passed in parallel

v-v-v

### Streams

<p>Represents a _stream_ of a future value or values</p> <!-- .element: class="fragment" -->

Values are independent of time <!-- .element: class="fragment" -->

Easy to combine with other streams <!-- .element: class="fragment" -->

Like Promises, can be passed around easily like normal data <!-- .element: class="fragment" -->

note:

- also known as Observables, will be using Observables interchangeably
- turbocharged Promises
- one or more future values
- value and error passed in parallel
- simple building blocks, allows for creating complex behavior

v-v-v

### Promises and Observables

Easy to combine multiple values into one <!-- .element: class="fragment" -->

Values and errors move in parallel <!-- .element: class="fragment" -->

Allows for declarative code where it matters <!-- .element: class="fragment" -->

note:

- allows easy use of combinators
- great for passing value/error to relevant portion
- expressive code in fewer lines

v-v-v

Concepts unique compared to imperative code  <!-- .element: class="fragment" -->

Makes your head hurt if only familiar with imperative code <!-- .element: class="fragment" -->

<img src="img/foochan.jpg" style="width: 30%"> <!-- .element: class="fragment" -->

note:

- async data is _hard_
- abstract
- forces into more declarative style further down the road
- introduces entirely new ways of screwing stuff up
