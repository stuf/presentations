## Brief history of async JS

---

### The Players

Events

Callbacks

Promises

Streams

<small>There are more, but these ones are the most relevant</small>

---

### Generally speaking

Advantages:

- Non-blocking
- Parallel operations 
- ???

note:

- fs.readFile and readFileSync for a 1GB file
- Like above, perform task only when required
- Wait until the desired data is there

---

### Events

Supported since Netscape times

Pub-sub messaging

Difficult to pass result around

Combining separate results is onerous

note:

- explicit subscription, "only interested in this"
- solutions concentrate on handling the result there and then
- passing value around requires laborous solutions, like event aggregation
- this is perfectly fine for some things, but we can do better

---

### Callbacks / CPS

Node.js introduced continuous-passing style (callbacks) for async

Operation is given function to call when done

The Callback Hell is real

Difficult to pass result around

Combining separate results is onerous

note:

- base concept is old (1975)
- operation takes callback function as last param to call when done
- but same problems as events
- some workarounds exist, but solutions concentrate on handling the result there and then

---

### Promises

Introduced into JS fairly "recently"

_Proxy object_ for future data

Can be passed around like normal data

Gateway drug to Streams

note:

- old idea as well, studied since 1980's, concept from 1970's
- can be passed around to where the result is wanted
- it's just a box for eventual data
- value and error passed in parallel

---

### Streams

Represents a _stream_ of a future value or values

Values are independent of time

Like Promises, can be passed around easily like normal data

note:

- also known as Observables, will be using Observables interchangeably
- turbocharged Promises
- one or more future values
- value and error passed in parallel
- simple building blocks, allows for creating complex behavior

---

### Things worth noticing

Both Promises and Streams allow:

Combining multiple values into one

Values and errors in parallel

Allows for declarative code where it matters

note:

- allows easy use of combinators
- great for passing value/error to relevant portion
- expressive code in fewer lines

---

Conceps unique compared to imperative code

Makes your head hurt if only familiar with imperative code

<img src="img/sad_otter.jpg" style="width: 30%">

note:

- async data is _hard_
- abstract
- forces into more declarative style further down the road
- introduces entirely new ways of screwing stuff up
