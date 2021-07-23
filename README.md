# Integrating React with a Phoenix App


### Running the app

1. Clone this repo
2. cd react
3. mix deps.get
4. cd assets npm install
5. cd ../
6. mix phx.server
7. Navigate to  http://localhost:4000

### Building from scratch

#### Scaffold a Phoenix app

mix phx.new react-phoenix --no-ecto

* creating react/config/config.exs
* creating react/config/dev.exs
* creating react/config/prod.exs
* creating react/config/prod.secret.exs
* creating react/config/test.exs
* creating react/lib/react/application.ex

Fetch and install dependencies? [Yn] y
* running mix deps.get
* running mix deps.compile
* running cd assets && npm install && node node_modules/webpack/bin/webpack.js --mode development

cd react
mix phx.server

Navigate to  http://localhost:4000

#### Integrate React 

npm install --save react react-dom @babel/preset-react

###### Update .babelrc 

{
    "presets": [
        "@babel/preset-env",
        "@babel/preset-react" # add this line
    ]
}

###### Update webpack.config.js 

rules: [
{
    test: /\.(js|jsx)$/, # change this line
    exclude: /node_modules/,
    use: {
    loader: 'babel-loader'
    }
}

###### Update app.js with the following code 

import React from 'react';
import ReactDOM from 'react-dom';

import Hello from './components/hello'
ReactDOM.render(<Hello />, document.getElementById('root'))


###### Create a new file hello.js in /js/components 

import React from 'react';

export default class Hello extends React.Component {
  render() {
    return (<div>
      <p>Hello React</p>
    </div>
    )
  }
}

###### Replace templates/page/index.html.eex with the following

<div id="root"></div>

The page will autoreload after these changes and the react page will be rendered
