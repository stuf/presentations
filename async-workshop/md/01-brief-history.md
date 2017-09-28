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

Advantages:

- Non-blocking
- Parallel operations
- ???

note:

- fs.readFile and readFileSync for a 1GB file
- Like above, perform task only when required
- Wait until the desired data is there

v-v-v

### Events

Supported since Netscape times

Pub-sub messaging

Difficult to pass result around

Combining multiple results is annoying

Small cost upfront, hidden costs

note:

- explicit subscription, "only interested in this"
- solutions concentrate on handling the result there and then
- passing value around requires laborous solutions, like event aggregation
- this is perfectly fine for some things, but we can do better

v-v-v

### Callbacks / CPS

Node.js began using continuous-passing style (callbacks) for async

Operation is given function to call when done

The Callback Hell is real

Difficult to pass result around

Combining multiple results is annoying

note:

- base concept is old (1975)
- operation takes callback function as last param to call when done
- but same problems as events
- some workarounds exist, but solutions concentrate on handling the result there and then
- not really meant for combinators etc.

v-v-v

### Promises

Introduced into JS fairly "recently"

_Proxy object_ for future data

Can be passed around like normal data

Gateway drug to Streams

note:

- old idea as well, studied since 1980's, concept from 1970's
- popularized as deferreds back in 2011 by jquery, among others
- can be passed around to where the result is wanted
- it's just a box for eventual data
- value and error passed in parallel

v-v-v

### Streams

Represents a _stream_ of a future value or values

Values are independent of time

Easy to combine with other streams

Like Promises, can be passed around easily like normal data

note:

- also known as Observables, will be using Observables interchangeably
- turbocharged Promises
- one or more future values
- value and error passed in parallel
- simple building blocks, allows for creating complex behavior

v-v-v

### Things worth noticing

Both Promises and Streams allow:

Combining multiple values into one

Values and errors in parallel

Allows for declarative code where it matters

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
