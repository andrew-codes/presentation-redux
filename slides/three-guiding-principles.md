## Three Guiding Principles


### There is a single source of truth

Note:
- meaning all state is stored in a single object
- there is not duplication of state


### State is read-only

Note:
- when reading application state, it is immutable


### Mutations are made via pure functions

Note:
- functions are pure if they return the same output, when given the same input
- meaning they have no side-effects


### Pure Functions FTW!
- hot reloading, <!-- .element: class="fragment" data-fragment-index="1" -->
- time travel, <!-- .element: class="fragment" data-fragment-index="2" -->
- undo/redo, <!-- .element: class="fragment" data-fragment-index="3" -->
- record and replay <!-- .element: class="fragment" data-fragment-index="4" -->

Note:
By using pure functions, we get these as freebies.
