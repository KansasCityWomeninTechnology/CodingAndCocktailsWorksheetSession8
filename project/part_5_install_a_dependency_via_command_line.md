### Part 5: Install a dependency via command line {#part-5-install-a-dependency-via-command-line}

Just like the init command, **npm** provides an easy way to add a dependency via command line, too. In this part, we'll add a dependency on **lodash** using this method.

{% hint style='info' %}
**Lodash** is a library that helps you manipulate JSON objects in JavaScript. This can be very handy if you want to:
- sort an array (alphabetically, or in some other way)
- replace words in a string
- generate a random number
- and much much more!

Lodash - along with hundreds of other libraries - are available via **npm**. The URL for this is: https://www.npmjs.com/package/lodash

This is the **home** of the library on **npm**, where you can find links to the author(s), documentation, support, etc. Try substituting the last part with another library, such as **jquery**.
{% endhint %}

1.  On the command line, type: `npm install --save lodash`

  {% hint style='danger' %}
  #### npm warnings

  This command will warn that you don't have a description or repository filled out in your _package.json_ file. You don't need to worry about this right now.
  {% endhint %}

2.  When it’s done, notice the new dependency is listed in the _package.json_ file. It also downloaded the lodash library to a folder called _node_modules_.

  ![](../images/node_modules-folder.png)
