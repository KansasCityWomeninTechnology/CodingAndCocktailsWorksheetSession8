## Install Browserify (Globally) {#browserify}

Browserify will allow you to easily consume new dependencies with the JavaScript **require** statement.
{% hint style='tip' %}
npm packages are constantly updating so the pictures and instructions may not be the latest version available.
{% endhint %}

1. On the command line, type `npm install -g browserify` <i class="fa fa-share fa-rotate-180"></i>.

  {% hint style='hint' %}
The `-g` flag means we're installing the **npm** Browserify package globally (across your computer's operating system). That means you'll be able to use Browserify in your CLI across multiple projects by typing `browserify <command>`, which we'll use in a little bit.
  {% endhint %}

1. It will show a progress bar (of sorts) as it installs.

  <!--
  {% hint style='danger' %}
  #### Sudo warnings & passwords
  The **sudo** prefix is like running an application as **root** or **administrator**. On a mac, you might get a warning like _Improper use of the sudo command could lead to data loss..._ We're not doing anything dangerous here, just installing the browserify tool via **npm**, which requires this level of system access.

  Also, when you type your password on the command line, you won't be able to see it. This is normal. Just type it as you would normally and press enter.
  {% endhint %}
  -->

1. When it’s done, it should look something like this:
  ![](../images/browserify-complete.png)
