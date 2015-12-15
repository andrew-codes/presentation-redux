## Data Flow

1. Dispatch an action
2. Redux Store calls a Reducer with (current state, action)
3. Reducer reduces state
4. Redux Store saves new state tree from output of all Reducers
5. Redux Store notifiies all listeners
6. Listeners get state via `getState()`
