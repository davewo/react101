# Setup React
## References

[react - Core react site](https://reactjs.org/)

[react-dom - React Dom integration extensions](https://reactjs.org/docs/react-dom.html)

[Bable - Javascript cross browser support](https://babeljs.io/)

## Install react and react-dom as a dependency:
``` 
npm i react react-dom -S
```

## Install Babel

Install babel-core, babel-loader, babel-preset-env and babel-preset-react as a dev dependency

``` 
npm i babel-core babel-loader babel-preset-env babel-preset-react -D
```

Add **.babelrc** file to provide the options for babel-loader

```
 {
   "presets": ["env", "react"]
 }
```


Add **src/index.html** file

``` 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>React101</title>
</head>
<body>
  <section id="index"></section>
</body>
</html>
```

## Install html-webpack-plugin as a dev dependency:

``` 
npm i html-webpack-plugin -D
```

Create file **webpack.config.js**

``` 
const HtmlWebPackPlugin = require("html-webpack-plugin");

const htmlPlugin = new HtmlWebPackPlugin({
  template: "./src/index.html",
  filename: "./index.html"
});

module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  },
  plugins: [htmlPlugin]
};
```

If you now run ```npm run start``` you should see index.html being generated in the dist folder.
Open index.html in the browser, the open the developer tools console window to see the output



Next, replace the contents of your **src/index.js** file to render a component:

``` 
import React from "react";
import ReactDOM from "react-dom";

const Index = () => {
  return <div>Hello React!</div>;
};

ReactDOM.render(<Index />, document.getElementById("index"));
```

If you now run ```npm run start``` should be compiled to display the react application.

Run ```open dist/index.html``` and you should see “Hello React” in your browser.

## Setup webpack-dev-server
```
 npm i webpack-dev-server -D
```

Change **package.json** start script 

```diff
"scripts": {
+   "start": "webpack-dev-server --mode development --open --hot",
-   "start": "webpack --mode development",
    "build": "webpack --mode production"
  },
```

Start webpack dev server on port 8080 (default)
``` 
npm run start
```

[Proceed to Step 3 - Setup Storybook](setup-storybook.md)
