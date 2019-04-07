---
layout: post
title: re·act and tail·wind
---

Recently, I've been having fun with writing front-end code using _utility-first_ CSS frameworks instead of full-blown toolkit ones like [Bootstrap](https://getbootstrap.com/) and [Bulma](https://bulma.io/). It helps me build and customize my page components immediately without having to write my own CSS from scratch. After seeing the attention that [Tailwind CSS](https://tailwindcss.com/docs/what-is-tailwind/) is getting from different communities and platforms, I decided to try it in one of my personal projects. It made styling pages more fun because it's so easy to use and the documentation is really intuitive. 

Since it's component-friendly, I tried using it on my following project with create-react-app to learn how well it fits with Single-Page Applications.

And now, I will help you setup your own create-react-app project with Tailwind CSS. Let's get started!

First, let's create a new ReactJS project with create-react-app.

```
npx create-react-app your-app-name
```

Next, we can easily install the Tailwind CSS module afterwards on our fresh create-react-app project without having to touch the actual scaffolding. Just run the following command on npm:

```
npm install tailwindcss --save-dev
```

After installing Tailwind CSS, we'll have to generate our configuration file which is in javascript format that is accessible and easy to get used to by using this command:

```
npx tailwind init tailwind.js
```

You can use any filename that you like but naming it `tailwind.js` as default is a recommendation from the documentation which is usually nice to follow.

Then, as what the documentation suggests, we'll add Tailwind as a [PostCSS](https://postcss.org/) plugin in our build chain. Install these peer dependencies via:

```
npm install postcss-cli autoprefixer --save-dev
```

Afterwards, we'll have to create a `postcss.config.js` file where we'll add Tailwind as a plugin by passing the path within.


```javascript
var tailwindcss = require('tailwindcss');

module.exports = {
  plugins: [
    tailwindcss('./path/to/your/tailwind.js'),
    require('autoprefixer'),
  ]
}
```

Your `tailwind.js` and `postcss.config.js` configuration files can be included in any part of your directory but right now, I just put it within the root level of my project.

Next, we'll have to create an _entry point_ so we'll be able to use Tailwind in our CSS. In this case, I always use the [recommendation](https://tailwindcss.com/docs/installation#3-use-tailwind-in-your-css) from the docs. 

Just copy and paste the code below within a new file named `tailwind.css` located in your project's `/src` directory or another custom folder within to separate your static and custom styles from generated ones. In my case, I created a custom `/styles` directory:

```css
/**
 * This injects Tailwind's base styles, which is a combination of
 * Normalize.css and some additional base styles.
 *
 * You can see the styles here:
 * https://github.com/tailwindcss/tailwindcss/blob/master/css/preflight.css
 *
 * If using `postcss-import`, use this import instead:
 *
 * @import "tailwindcss/preflight";
 */
@tailwind preflight;

/**
 * This injects any component classes registered by plugins.
 *
 * If using `postcss-import`, use this import instead:
 *
 * @import "tailwindcss/components";
 */
@tailwind components;

/**
 * Here you would add any of your custom component classes; stuff that you'd
 * want loaded *before* the utilities so that the utilities could still
 * override them.
 *
 * Example:
 *
 * .btn { ... }
 * .form-input { ... }
 *
 * Or if using a preprocessor or `postcss-import`:
 *
 * @import "components/buttons";
 * @import "components/forms";
 */

/**
 * This injects all of Tailwind's utility classes, generated based on your
 * config file.
 *
 * If using `postcss-import`, use this import instead:
 *
 * @import "tailwindcss/utilities";
 */
@tailwind utilities;

/**
 * Here you would add any custom utilities you need that don't come out of the
 * box with Tailwind.
 *
 * Example :
 *
 * .bg-pattern-graph-paper { ... }
 * .skew-45 { ... }
 *
 * Or if using a preprocessor or `postcss-import`:
 *
 * @import "utilities/background-patterns";
 * @import "utilities/skew-transforms";
 */
```

After pasting this code and saving the file, we'll now install `npm-run-all` as our tooling to run our npm scripts in parallel or sequential order. This is not an actual requirement but I highly recommend it especially to Windows users. This CLI tool helps so we can run our scripts in cross-platform.

```
npm install npm-run-all --save-dev
```

Next, we'll have to configure our `package.json` file to build our CSS and start our local create-react-app server. The `scripts` section will now look similar to this:

```json
"scripts": {
    "start": "npm-run-all --parallel watch:css start:react",
    "build": "npm-run-all build:css build:react",
    "build:css": "postcss src/styles/tailwind.css -o src/index.css",
    "watch:css": "postcss src/styles/tailwind.css -o src/index.css -w",
    "start:react": "react-scripts start",
    "build:react": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
```

We'll now be able to run the `npm start` script within npm to build our files and start our server.

```
npm start
```

Lastly, to test if Tailwind CSS is working within your components, we'll just have to import the generated `index.css` file and add a utility class from Tailwind's documentation within our JSX like so:

```javascript
import React from "react";
import ReactDOM from "react-dom";
import "./index.css";

const App = () => {
  return <div className="bg-blue">Hello World!</div>
};

ReactDOM.render(<App />, document.querySelector("#root"));
```

Here's how it looks on the browser!

![Hello World Sample](https://i.imgur.com/GKXoFFh.png)
<figcaption>
    This is a screenshot in 300% zoom made with <a href="https://www.screely.com/">Screely</a>.
</figcaption>

<hr/>

That's a wrap! Thanks for reading and I hope that I was able to introduce this setup properly.