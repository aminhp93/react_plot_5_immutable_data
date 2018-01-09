## 5 - Immutable Data

[https://academy.plot.ly/react/5-immutable-data/](https://academy.plot.ly/react/5-immutable-data/)

1.  shouldComponentUpdate(nextProps) {
        return false;
    }

2. 
`
var object1 = {
    twitter: '@mxstbr'
};

var object2 = {
    twitter: '@mxstbr'
};

console.log(object1 === object2); // -> false
`

`
var object1 = fromJS({
    twitter: '@mxstbr'
});

var object2 = fromJS({
    twitter: '@mxstbr'
});

console.log(object1.equals(object2)); // -> true 🎉
`

3. fromJS, toJS
`
case 'SET_SELECTED_DATE':
  return Object.assign({}, state, {
    selected: {
      date: action.date,
      temp: state.selected.temp
    }
  });
`
`
case 'SET_SELECTED_DATE':
  return state.setIn(['selected', 'date'], action.date);
`

4. 
`
if (this.props.data.list){
    currentTemp = this.props.data.list[0].main.temp;
}
`

`
if (this.props.redux.getIn(['data', 'list'])) {
    currentTemp = this.props.redux.getIn(['data', 'list', '0', 'main', 'temp']);
}
`