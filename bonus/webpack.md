### Webpack

Earlier we used **Browserify** to bundle our JavaScript files. **Webpack** is another tool that developers use as it offers similar & yet more robust capabilities. However, after using **Browserify**, it can be intimidating to use **Webpack**, so let's tackle it.

In your CLI, make sure `pwd` [your current working directory] is _packagesproject_.

  1. First, we need to install **Webpack**. Instead of installing it globally [like we did with **Browserify**], we're going to install it to our project. In your CLI, type: `npm install webpack --save-dev`  

  {% hint style='tip' %}
  This installs the **Webpack** package and adds it to your _package.json_ in the `devDependencies` section. We install it as a dev dependency since we only want to use the package for the development of our project and we won't be including **Webpack** with our application in production.

   You can install either **Browserify** or **Webpack** globally [with `-g` flag or locally to the project]. We're installing **Webpack** to our project to illustrate the difference.
  {% endhint %}
