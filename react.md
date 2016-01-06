# React



# React
- view framework 
- implementira api za komponente
- implementira manipulacijo doma (virtual dom, diff)
- Opcijski JSX "template", ki se transpajla v javascript 



## Minimalna komponenta
```
var HelloMessage = React.createClass({
  render: function() {
    return <div>Hello {this.props.name}</div>;
  }
});

ReactDOM.render(<HelloMessage name="John" />, mountNode);
```



## Component specs
[component lifecycle](https://facebook.github.io/react/docs/component-specs.html)
- required render()
- displayName
- propTypes
- getInitialState
- getDefaultProps 
- mixins
- props, state, contex, refs



## Component lifecycle
- componentWillMount // 1, pred render
- componentWillUnmount // 1, pred unmount
- componentDidMount // 1, po render
- componentWillReceiveProps(nextProps) // n, na props
- shouldComponentUpdate(nextProps, nextState) // n, pred render
- componentWillUpdate // pred render update
- componentDidUpdate //



## React setup hello projekt
### Branch step1
- nov projekt (npm, webpack, struktura, html)
- main.js (vstopna točka)
- app.js (helloworld komponenta)



### Branch step2-components
- InputComponent (textbox)
- InputList (seznam inputov)
- App container 



## Redux
- state kontroler
- Akterji: actions, reducers, store



## Redux store
```
// create
var store = createStore(reducer)
```
```
// dispatch
store.dispatch({
    type: 'AN_ACTION'
})

var asyncSayActionCreator = function (message) {
  return function (dispatch) {
    dispatch({
        type: 'SAY', 
        message
    })
  }
}

store.dispatch(asyncSayActionCreator('Hello'))
```
```
// subscribe
store.subscribe(function() {
    // retrieve latest store state here
    // Ex:
    console.log(store.getState());
})
```



## Redux refs.
- <http://redux.js.org/>
- <https://github.com/happypoulp/redux-tutorial>



### Branch step3-redux
- appActions, addItem
- appReducer
- combineReducers
- createStore
- Provider



### Branch step4-grommet
- Grommet ui framework (hp)
- app, header, title, docs 
- <http://www.grommet.io/>
- <http://www.grommet.io/docs/develop>
- <https://github.com/grommet/grommet>



# Reference
- <http://facebook.github.io/react/>
- <http://facebook.github.io/react/docs/thinking-in-react.html>
- <https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0>
- <http://redux.js.org/>
- <https://github.com/happypoulp/redux-tutorial>
- <http://teropa.info/blog/2015/09/10/full-stack-redux-tutorial.html>
