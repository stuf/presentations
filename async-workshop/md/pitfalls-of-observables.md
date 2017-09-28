## Pitfalls of Observables

---

## Documentation can be confusing

Terminology varies between libraries

<small>RxJS's hot and cold Observables, Kefir's activation and deactivation</small>

Does not explain concepts well for the uninitiated <!-- .element: class="fragment" -->

But Kefir's documentation is a positive exception <!-- .element: class="fragment" -->

---

>Projects each element of an observable sequence into a new sequence of observable sequences by incorporating the element's index and then transforms an observable sequence of observable sequences into an observable sequence producing values only from the most recent observable sequence.
>
><small>RxJS on `flatMapLatest`</small>

This is not the case anymore. <!-- .element: class="fragment" -->

It has been improved.  <!-- .element: class="fragment" -->

---

>Transform the items emitted by an Observable into Observables, and mirror those items emitted by the most-recently transformed Observable.
>
><small>RxJS on `flatMapLatest`</small>

---

<img src="img/wat.jpg">

In simple English please <!-- .element: class="fragment" -->

note:

- one of the rare cases where semantic satiation kicks in when reading documentation

---

>Like `flatMap`, but repeats events only from the latest added observable i.e., **switching from one observable to another**.
>
><small>Kefir docs on `flatMapLatest`</small>

(ㆁωㆁ*) Much better. <!-- .element: class="fragment" -->
