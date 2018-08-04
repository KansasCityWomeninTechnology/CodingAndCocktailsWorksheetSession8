## **npm** Scripts & Browserify-like Webpack

Earlier we used **Browserify** to bundle our JavaScript files. **Webpack** is another tool that developers use as it offers similar & yet more robust capabilities. However, after using **Browserify**, it can be intimidating to use **Webpack**, so let's tackle it.

{% hint style='tip' %}
##### Hey Slacker!

Remember, we're here to help.
Join the KCWiT #codingandcocktails Slack Channel: [kcwit.slack.com](http://kcwit.slack.com)
{% endhint %}

In your CLI, make sure `pwd` [your current working directory] is _packagesproject_.

1. First, we need to install **Webpack**. Instead of installing it globally [like we did with **Browserify**], we're going to install it to our project. In your CLI, type: `npm install webpack@3.11.0 --save-dev` <i class="fa fa-share fa-rotate-180"></i>.  

  {% hint style='tip' %}
This installs a specific version of the **Webpack** package and adds it to your _package.json_ in the `devDependencies` section. We install it as a dev dependency since we only want to use the package for the development of our project, and we won't be including **Webpack** with our application in production.

You can install either **Browserify** or **Webpack** globally [with `-g` flag or locally to the project]. We're installing **Webpack** to our project to illustrate the difference.
  {% endhint %}

1. You can use **Webpack** similarly to the way we used **Browserify**. Delete the _bundle.js_ file from your project and in your CLI type `webpack index.js bundle.js` <i class="fa fa-share fa-rotate-180"></i>.

  What's that? You got an error? `'webpack' is not recognized as an internal or external command, operable program or batch file.` Or simply `webpack: command not found`?

  Oh yea, that's because we installed **Webpack** locally.

  Let's use the `webpack` command out of our project's local _node_modules_. In your CLI, type `./node_modules/.bin/webpack index.js bundle.js` <i class="fa fa-share fa-rotate-180"></i>.

  <img src="../images/webpack-command-location.png" style="max-width: 50%;" />

  {% hint style='tip' %}
If you open the generated _bundle.js_ file, you'll notice it's larger than the **Browserify** version. Your code is in there (might use Atom's search b/c it's a bit hidden in there), **lodash** is in there **and** there is some extra **Webpack** code in there that enables **Webpack** to do its own thing.
  {% endhint %}

1. Obviously having to type `./node_modules/.bin/webpack index.js bundle.js` every time you want to build your file isn't ideal. Let's add an **npm** script to make our lives easier. Open your _package.json_ file in Atom.

1. There is already a script in there, look for the following:
  ```json
  "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
  },
  ```

  Add a comma at the end of the line that starts with `"test"` (after the ending quote) and press `Enter`.

  On the new line, type `"bundle": "webpack index.js bundle.js"` <i class="fa fa-share fa-rotate-180"></i>.

  It should look like the following:

  ![](../images/npm-scripts.png)

  {% hint style='tip' %}
Whoa. Why didn't you have to include the `./node_modules/.bin/` in front of `webpack`?

That's because since the package is installed locally to the project, the **npm** script can find the command by simply using the command name.
  {% endhint %}

1. Now, you can run the **npm** script by typing the following in your CLI by typing `npm run bundle` <i class="fa fa-share fa-rotate-180"></i>.

  {% hint style='tip' %}
Anything in the **scripts** portion can be run with `npm run <propertyName>`, where **propertyName** is whatever you've set in the quotes before the `:`.
  {% endhint %}



### Webpack with Config

So using **Webpack** like **Browserify** was pretty straightforward, but you're probably not going to find anything like that in a real life project. So let's jump into a more realistic example.

1. In your _packagesproject_ directory, create a new file and name it _webpack.config.js_.

1. Open the _webpack.config.js_ in Atom and add the following and save the file:

  ```javascript
  module.exports = {
      entry: './index.js',
      output: {
        filename: './bundle.js'
      }
  };
  ```

  {% hint style='tip' %}
The **module.exports** is a bit out of scope for tonight's session. We'll cover it a bit next month, but it basically exposes the **entry** and **output** properties so that the **Webpack** utility can find and use them.

**entry** is our main JavaScript file [like the **main** property we specified in our _package.json_]

**output** can take multiple properties, but we're only going to use one, the **filename** - which is the file name we want to use for the bundled JavaScript file.
  {% endhint %}

1. Now that you have the config file set up, you can use the `webpack` command by itself to generate the _bundle.js_ file. Since we don't have **Webpack** installed globally, we'd still have to do `./node_modules/.bin/webpack`, so let's add a couple scripts to make our lives easier.

1. Open _package.json_ in Atom and add the following scripts:

  ```json
  "build": "webpack",
  "minbuild": "webpack -p",
  "watch": "webpack --watch"
  ```

  {% hint style='tip' %}
Scroll up to our earlier example if you need a reminder on where to add these.
  {% endhint %}

1. Let's try running each of these scripts. In your CLI, type `npm run build` <i class="fa fa-share fa-rotate-180"></i>.

  This command works just like our **Browserify** or earlier **Webpack** commands, the _bundle.js_ has our code, **lodash**, and some **Webpack** code.

1. Now, let's do the one with the `-p` flag. In your CLI, type `npm run minbuild` <i class="fa fa-share fa-rotate-180"></i>

  The `-p` flag is short for **production** and using it makes your _bundle.js_ file ready for production. What does that mean? In short, it **minifies** the _bundle.js_ file. Open the _bundle.js_ file in Atom and take a look. It should like a bunch of random letters/numbers all squished together.

  {% hint style='info' %}
**Minification** reduces the file size, which in turn means the file can load faster in a browser and boost your application's performance. Part of the minification process removes extra whitespace [spaces between words/logic, line breaks -- all of it]. It takes your very descriptive variable/method names and replaces them with a few letters that appear random.

They just appear random, the variable/method names still match up in the code base, so your application still runs the same as it did before. [As an example, it takes the variable `wine` and replaces it everywhere in the code with `w`.]

When you're working on a large project, the code can get very large, so minifying helps to make the application's performance better with files reduced in size.
  {% endhint %}

1. Watch, this is going to be fun [pun intended]. In your CLI, type `npm run watch` <i class="fa fa-share fa-rotate-180"></i>.

  **Webpack** is now watching your code for changes. That means you can update the code in _index.js_ and when you save the file, **Webpack** will automatically update the _bundle.js_ file. If you reload _index.html_ in Chrome, you'll see the updates without having to run a command.

  {% hint style='tip' %}
  In order to stop the **watch** command from continuing to run in the CLI, we need to stop it. On a Mac, the shortcut is **cmd** + **c**. On Windows, the shortcut is **ctrl** + **c**.
  {% endhint %}

1. So that's fun, but refreshing is one more step. We can do better. In your CLI, type `npm install webpack-dev-server@webpack-3 --save-dev` <i class="fa fa-share fa-rotate-180"></i>

  This is installing another **Webpack** package using a custom npm version tag "webpack-3". The creators of Webpack mapped this tag to a version of a Webpack release and works in the same way as "latest".

1. Open your _package.json_ in Atom and add the following script:

  `"start": "webpack-dev-server --open"`

  This script will start the **webpack-dev-server**.

1. Open your _webpack.config.js_ file in Atom. Add a `,` after the closing curly brace for `output` and add the following:

  ```json
  devServer: {
        contentBase: './'
  }
  ```

  This is telling the **webpack-dev-server** what directory to look for file changes, which is the root/top-level directory of our project.

  The _webpack.config.js_ file should look like this:

  ```javascript
  module.exports = {
        entry: './index.js',
        output: {
          filename: './bundle.js'
        },
        devServer: {
          contentBase: './'
        }
  };
  ```

1. In the CLI, type `npm run start` <i class="fa fa-share fa-rotate-180"></i>.

  The dev server is now watching your code and will automatically reload the browser, if you make any changes.

1. Open _index.html_ in Chrome, and open _index.js_ in Atom. If you can, make them side-by-side, so you can see Chrome, while you make a change to the code.

1. Update `white` in _index.js_ to `blue` and save the file. Chrome should automagically refresh and show you the new code.

  ![](https://media.giphy.com/media/OUwzqE4ZOk5Bm/giphy.gif)
