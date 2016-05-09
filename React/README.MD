# React Demo

### Demo1 - render

```
ReactDOM.render(
    React.createElement("h2", null, "Hello, world!"),
    document.getElementById('container')
);	
```

### Demo2 - jsx

```
ReactDOM.render(
    <h2>Hello, world!</h2>,
    document.getElementById('container')
);
```

### Demo3 - jsx with js

```
var hello = "Hello, JSX with Javascript!";
ReactDOM.render(
    <h2>{ hello }</h2>,
    document.getElementById('container')
);
```

### Demo4 - first component

```
var Hello = React.createClass({
    render: function() {
        var hello = "Hello, first component!";
        return <h2>{ hello }</h2>;
    }
});
ReactDOM.render(
    <Hello />,
    document.getElementById('container')
);
```

### Demo5 - with props

```
var Hello = React.createClass({
    propTypes: {
        name: React.PropTypes.string.isRequired
    },
    render: function() {
        var hello = "Hello, " + this.props.name;
        return <h2>{ hello }</h2>;
    }
});
ReactDOM.render(
    <Hello name="component with props"/>,
    document.getElementById('container')
);
```

### Demo6 - dom node

```
var Hello = React.createClass({
    componentDidMount: function() {
        var that = this;
        setTimeout(function(){
            that.refs.test.innerHTML = 'Hello, reset DOM Node innerHTML';
        }, 2000);
    },
    render: function() {
        return (
            <div>
                <h2 ref="test">
                    Hello, get dom node!
                </h2>
            </div>
        );
    }
});

ReactDOM.render(
    <Hello />,
    document.getElementById('container')
);
```

### Demo7- state

```
var Hello = React.createClass({
    getInitialState: function() {
        return {
            flag: true
        };
    },
    doClick: function() {
        this.setState({
            flag: !this.state.flag
        });
    },
    render: function() {
        return(
            <h2 onClick={ this.doClick }>
                Hello, { this.state.flag.toString() }
            </h2>
        );
    }
});
ReactDOM.render(
    <Hello/>,
    document.getElementById('container')
);
```

### Demo8 - state run once

```
var Name = React.createClass({
    getInitialState: function() {
        return {
            name: this.props.name
        };
    },
    componentWillReceiveProps: function(nextProps) {
        return;
        
        this.setState({
            name: nextProps.name
        });
    },
    render: function() {
            return (
                <span > 
                    Hello, {this.state.name}
                </span>
            );
    }
});
var Hello = React.createClass({
    getInitialState: function() {
        return {
            name: 'Li Lei'
        };
    },
    componentDidMount: function() {
        var that = this;
        setTimeout(function(){
            that.setState({
                name: 'Han Meimei'
            })
        }, 2000)
    },
    render: function() {
        return(
            <h2>
                <Name name={ this.state.name } />
            </h2>
        );
    }
});
ReactDOM.render(
    <Hello />,
    document.getElementById('container')
);	
```

### Demo9 - inline style

```
var h1Style = {
    color: 'red',
    backgroundColor: '#ccc',
    WebkitTransition: 'all',
    msTransition: 'all'
};

var Hello = React.createClass({
    render: function() {
        return <h2 style={ h1Style } className="test">Hello, inline styles！</h2>;
    }
});

ReactDOM.render(
    <Hello />,
    document.getElementById('container')
);
```

### Demo10 - children

```
var Hello = React.createClass({
    render: function() {
        return (
            <h2>
                { this.props.children }
            </h2>
        );
    }
});

ReactDOM.render(
    <Hello>Hello, children！</Hello>,
    document.getElementById('container')
);	
```