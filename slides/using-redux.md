## Using Redux


### Setting up a Redux Store

```javascript
const initialDataFromServer = {
	Timesheet: {
		items: []
	},
	Budget: {
		selectedBudget: null,
		budgets: []
	}
}

import { createStore, combineReducers } from 'redux';
import { Reducer as Timesheet } from './modules/Timesheet';
import { Reducer as Budget } from './modules/Budgets';

const reducers = combineReducers({
	Timesheet,
	Budget
});
let store = createStore(reducers, initialDataFromServer);
```

Note:
- load page with data we want to bootstrap into our state
- we want to utilzie Timesheet and Budgets on the same page
	- we can use Redux to combine our reducers into a single, root Reducer
	- notice the shape of our initial state mirros our combined reducer's shape
- use Redux to create a store from our combined reducers and initial data


### Mutations and Data Flow

1. Dispatch an action <!-- .element: class="fragment" data-fragment-index="1" -->
2. Redux Store calls a Reducer with (current state, action) <!-- .element: class="fragment" data-fragment-index="2" -->
3. Reducer reduces state <!-- .element: class="fragment" data-fragment-index="3" -->
4. Redux Store saves new state tree from output of all Reducers <!-- .element: class="fragment" data-fragment-index="4" -->
5. Redux Store notifiies all listeners <!-- .element: class="fragment" data-fragment-index="5" -->
6. Listeners get state via getState() <!-- .element: class="fragment" data-fragment-index="6" -->


#### 1. Dispatching an Action

```javascript
import * as actions from './modules/Timesheet';

store.dispatch(actions.addAssetToTimesheet('Story:10001'));
```


#### 2. Action Passed to Reducer with Current State

```javascript
export function timesheetReducer(state, action) {
	switch(action.type) {
		case 'AddAssetToTimesheet':
			let newState = Object.assign({}, state);
			newState.items.push(action.payload);
			return newState;
	}
	default:
		return state;
}
```

Note:
The switch statement is a bit awkward. We can refactor the matching of an action type to reducer method; something we already have done with `createReducer`.


#### 2.5 Refactored Reducer Creation

```javascript
import { createReducer } from './lib/utils/redux';

const initialState = {
	items: []
};

export function createReducer(initialState, {
	['AddAssetToTimesheet']: (state, action) => {
		// do our thing
	},
	['AnotherTimesheetAction']: (state, action) => {
		// do a different thing
	}
});
```


#### 3. Notifications of New state

```javascript
store.getState(); // => new state
```
