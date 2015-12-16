## What is state?

- which buttons are active <!-- .element: class="fragment" data-fragment-index="1" -->
- which inputs are hovered or selected <!-- .element: class="fragment" data-fragment-index="1" -->
- which view is showing <!-- .element: class="fragment" data-fragment-index="1" -->
- even the URL <!-- .element: class="fragment" data-fragment-index="1" -->


### What is state:
any data representing the current snapshot of the UI. <!-- .element: class="fragment" data-fragment-index="1" -->


## Pain Points

- cascading updates <!-- .element: class="fragment" data-fragment-index="1" -->
- non-deterministic mutations <!-- .element: class="fragment" data-fragment-index="2" -->
- difficulty reasoning about <!-- .element: class="fragment" data-fragment-index="3" -->

We lose control over the when, why, and how of our state. <!-- .element: class="fragment" data-fragment-index="4" -->

Note:
- cascading updates: when a model can update another model, the a view can update a model, which updates another model, which updates another view...
- non-deterministic mutations makes it hard to reproduce bugs or add new features reliably
- all this leads to a very difficult time trying to reason about our state
	- We have lost control over the **when, why, and how of state management**


The Problem: **state management is hard.** <!-- .element: class="fragment" data-fragment-index="1" -->

and we manage a lot of state. <!-- .element: class="fragment" data-fragment-index="2" -->

...a lot, a lot. <!-- .element: class="fragment" data-fragment-index="3" -->

no really, more than you. <!-- .element: class="fragment" data-fragment-index="4" -->


## Motivations Behind Redux

- make state mutations predictable <!-- .element: class="fragment" data-fragment-index="1" -->
- make state easier to reason about <!-- .element: class="fragment" data-fragment-index="2" -->
