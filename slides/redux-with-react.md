## Redux with React

- not React specific <!-- .element: class="fragment" data-fragment-index="1" -->
- connector glue in package: react-redux <!-- .element: class="fragment" data-fragment-index="1" -->


### react-redux

- Provider component<!-- .element: class="fragment" data-fragment-index="1" -->
- connect function <!-- .element: class="fragment" data-fragment-index="2" -->


### Provider

```javascript
import { createStore}  from 'redux';
import { Provider }  from 'react-redux';
import TimesheetComponent from './components/Timesheets/Timesheet';

// const reducer = combineReducers({reducer1, reducer2, Timesheet}); // etc.
let store = createStore(reducer, initialData);

React.render(
	<Provider store={store}>
		<TimesheetComponent />
	</Provider>
);
```


### connect()()

```javascript
import { connect } from 'redux-react';

class MyComponent extends React.Component {
	render() {
		return <span>{this.props.myComponentText}</span>
	}
}

export default connect(mapStateToProps, mapActionsToProps)(MyComponent);
```


#### Mapping State/Actions to Props

```javascript
import { bindActionCreators } from 'redux';

function mapStateToProps(state) {
	return {}; // sub-set of state for this component.
}

function mapActionsToProps(dispatch) {
	return {
		actions: bindActionCreators(actionCreators, dispatch)
	};
}
```


#### connect()()

- augments a given component with additional funcitonality
- high order component or higher order function
- original component used with or without connect
	- still only relies on props


### Action Usage

```javascript
import { connect } from 'redux-react';

class MyComponent extends React.Component {
	render() {
		const {
			actions: {
				addAssetToTimesheet
			}
		} = this.props;
		return <span onClick={addAssetToTimesheet('Story:10001')}></span>
	}
}

export default connect(mapStateToProps, mapActionsToProps)(MyComponent);
```
