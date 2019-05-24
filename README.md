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



### References

[The Official Journal Blog](https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658)
