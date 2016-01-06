# [React](http://facebook.github.io/react/) IF component

> React component for conditional rendering of embedded elements or props

## Description
In React component code you can often deal with construction like this:
```javascript
var loginButton;
if (loggedIn) {
  loginButton = <LogoutButton />;
} else {
  loginButton = <LoginButton />;
}

return (
  <nav>
    <Home />
    {loginButton}
  </nav>
);
```
With help of **React IF component** you can replace such construction:
```javascript
var Node = require('react-if-component');

return (
  <nav>
    <Home />
    <Node if={loggedIn} then={LogoutButton} else={LoginButton}>
  </nav>
);
```
## Install
* NPM
```shell
$ npm install --save react-if-component
```
* Bower
```shell
$ bower install --save react-if-component
```

## Usage
```javascript
var React = require('react')
  , ReactDOM = require('react-dom')
  , Node = require('react-if-component')
;

var Bar = React.createClass({
    render: function() {
        return (
            <b>Bar</b>
        );
    }
});

var Foo = React.createClass({
    render: function() {
        return (
            <b>Foo</b>
        );
    }
});

var Index = React.createClass({
    render: function() {
        return (
            <div>
              <Node if={true} then='true' />

              <Node if={true} then='true' else='false' />

              <Node if={false} then='true' else='false' />

              <Node if={true} then={1+1} else={0+0} />

              <Node if={true} then={Bar} else={Foo} />

              <Node if={false} then={Bar} else={Foo} />

              <Node if={true} then={<Bar one='1' two='2' />} else={<Foo one='1' two='2' />} />

              <Node if={true}>
                <b>true</b>
              </Node>

              <Node if={false}>
                <Node else><b>false</b></Node>
              </Node>

              <Node if={true}>
                <Node then><b>true</b></Node>
                <Node else><b>false</b></Node>
              </Node>

              <Node if={true}>
                <i>begin</i>
                <Node then><b>true</b></Node>
                <Node else><b>false</b></Node>
                <i>end</i>
              </Node>

              <Node if={true}>
                <b>true</b>
                <Node if={true} then='true' />
              </Node>
            </div>
        );
    }
});

ReactDOM.render(<Index />, document.getElementById('body'));
```

## License
**react-if-component** is released under the **MIT** license.
