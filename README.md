## APOGEE React App From Scratch

This is my attempt to create React App from Scratch and keep log on what commands I'm using to do this again for other projects.
```
npm init
```

This command will produce `package.json`

Now, we can start version control using git
```
git init
```

Then create this structure in the project folder
```
.
+-- public
+-- src
```

Create a `.gitignore` file to exclude `node_modules` and `dist`.

Our `public` directory will handle any static assets. So, we put our `index.html` file inside `public` directory.

You can name your built script whatever you like, but I’ll be using `bundle.js` for this project.

### Babel

Next, we need to make sure the code we write can be compiled, so we’ll need Babel.

We can install Babel using this commands:
```
npm install --save-dev @babel/core
npm install --save-dev @babel/cli
npm install --save-dev @babel/preset-env
npm install --save-dev @babel/preset-react
```

We can also do this by combining the npm install
```
npm install --save-dev @babel/core @babel/cli @babel/preset-env @babel/preset-react
```

`babel-core` is the main babel package — We need this for babel to do any transformations on our code. `babel-cli` allows you to compile files from the command line. [`preset-react`](https://babeljs.io/docs/en/babel-preset-react) and [`preset-env`](https://babeljs.io/docs/en/babel-preset-env) are both presets that transform specific flavors of code — in this case, the `env` preset allows us to transform ES6+ into more traditional javascript and the `react` preset does the same, but with JSX instead.

In the project root, create a file called `.babelrc`. Here, we’re telling babel that we’re going to use the `env` and `react` presets.

```
{
  "presets": ["@babel/env", "@babel/preset-react"]
}
```

Babel also has a ton of plugins available that can be used if you only need to transform specific features or some feature you need isn’t covered by `env`. We won’t worry about those for now, but you can check them out [here](https://babeljs.io/docs/plugins/).

### Webpack
Now we need to acquire and configure Webpack. We’ll need a few more packages, and you’ll want to save these as dev dependencies: 

```
npm install --save-dev webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader
```

Webpack uses [loaders](https://webpack.js.org/loaders/) to process different types of files for bundling. It also works easily alongside the development server that we’re going to use to serve our React project in development and reload browser pages on (saved) changes to our React components. In order to utilize any of this though, we’ll need to configure Webpack to use our loaders and prepare the dev server.

Create a new file at the root of the project called `webpack.config.js`. This file exports an object with webpack’s configuration.

We set up `webpack-dev-server` in the devServer property. This doesn’t require much for our needs — just the location we’re serving static files from (such as our index.html) and the port we want to run the server on. Note that `devServer` also has a `publicPath` property. This `publicPath` tells the server where our bundled code actually is.

That last bit might have been a little confusing — Pay really close attention here: `output.publicPath` and `devServer.publicPath` are different. Read both entries. Twice.

Finally, since we want to use [Hot Module Replacement](https://webpack.js.org/guides/hot-module-replacement/) so we don’t have to constantly refresh to see our changes. All we do for that in terms of this file is instantiate a new instance of the plugin in the [plugins](https://webpack.js.org/configuration/plugins/) property and make sure that we set `hotOnly` to `true` in `devServer`. We still need to set up one more thing in React before HMR works, though.

We’re done with the heavy setup. Now let’s get React working!

### React

First, we’ll need to get two more packages: `react` and `react-dom`. Go ahead and save those as regular dependencies.

```
npm install --save react react-dom
```

We’ll need to tell our React app where to hook into the DOM (in our `index.html`). Create a file called `index.js` in your `src` directory. This is a very small file that does a lot in terms of your React app. Check it out.

```
import React from "react";
import ReactDOM from "react-dom";
import App from "./App.js";
ReactDOM.render(<App />, document.getElementById("root"));
```

create another file in `src` called `App.js` and `App.css`




### References

[The Official Journal Blog](https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658)
