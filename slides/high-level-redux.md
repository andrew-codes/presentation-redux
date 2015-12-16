## High-Level Redux

- Actions <!-- .element: class="fragment" data-fragment-index="1" -->
- Action Creators <!-- .element: class="fragment" data-fragment-index="2" -->
- Reducers <!-- .element: class="fragment" data-fragment-index="3" -->
- a Redux Store <!-- .element: class="fragment" data-fragment-index="4" -->


### Actions

- describe something that happened  <!-- .element: class="fragment" data-fragment-index="1" -->
- used to send data from application to store <!-- .element: class="fragment" data-fragment-index="2" -->


#### Example Action

```javascript
export const AddAssetToTimesheetAction = {
	type: 'AddAssetToTimesheet',
	payload: {
		oidToken: 'Story:10001',
		name: 'A Story Name',
		...otherAssetInfo
	}
};
```

Note:
- actions are just plain JavaScript objects
- manually creating this object every time we want to add an asset to timesheet would be cumbersome


### Action Creators

- functions that create actions <!-- .element: class="fragment" data-fragment-index="1" -->
- action creators don't dispatch actions <!-- .element: class="fragment" data-fragment-index="2" -->

Note:
- dry up using actions by creating a function to stamp them out
- easier to re-use actions
- easier to test
- more portable


#### Example Action Creator

```javascript
export function AddAssetToTimesheet(asset) {
	return {
		type: 'AddAssetToTimesheet',
		payload: asset
	};
}
```


### Reducers

- describe state transitions <!-- .element: class="fragment" data-fragment-index="1" -->
- are pure functions <!-- .element: class="fragment" data-fragment-index="2" -->
- independent sub-set of state <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- reducers do not store state
- instead, they describe how state mutates from State A to State B given some action
- sub-set of state is usually drawn along domain boundaries


#### Example Reducer

```javascript
export function timesheetReducer(state, action) {
	switch(action.type) {
		case 'AddAssetToTimesheet':
			// copy state, mutate it, return new state
			return newState;
	}
	default:
		return state;
}
```

Note:
- notice this reducer handles state for Timesheets only
- a reducer handles a discrete sub-set of application state
- we'll uses composition to combine several reducers to create a single store


### Redux Store

- storage of all application state <!-- .element: class="fragment" data-fragment-index="1" -->
- gives read-only access to state <!-- .element: class="fragment" data-fragment-index="2" -->
- provides updates via dispatching actions <!-- .element: class="fragment" data-fragment-index="3" -->
- registers listeners <!-- .element: class="fragment" data-fragment-index="4" -->


#### Example Redux Store Creation

```javascript
import { createStore } from 'redux';
import TimesheetReducer from './modules/Timesheet/Reducer';
let store = createStore(TimesheetReducer);
```
