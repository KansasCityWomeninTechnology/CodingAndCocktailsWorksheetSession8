### Package Locks

Package locks in **npm** are files that are meant to lock down the versions of the **npm** packages in your project. Versions can be a difficult thing to manage and one package updating could mean that your whole project is broken. Without a package lock file, `npm install` would install the most recent version [per the [SemVer](http://blog.npmjs.org/post/162134793605/why-use-semver) settings specified in your _package.json_], this means the dependencies that your dependencies use could be updated. That's where package lock files are useful. They list not only the versions of your immediate dependencies, but also all the versions of any nested [children, grandchildren] dependencies used.

When you run `npm install` in a directory, there is a hierarchy **npm** uses to determine which packages & versions to install.

  1. **_npm-shrinkwrap.json_**  
  If this file is found, the packages and versions defined in this file are installed.
  2. **_package-lock.json_**  
  If this file is found and _npm-shrinkwrap.json_ doesn't exist in your project, the packages and versions defined in this file are installed.
  3. **_package.json_**  
  If neither lock files were found, then **npm** falls back to this file for install.

When you run `npm install`, a _package-lock.json_ file is automatically generated (or updated if the file already exists). So you should already have a _package-lock.json_ file in your _packagesproject_ directory.

Make sure your `pwd` [current working directory] in your CLI is _packagesproject_ and let's look a bit more into these lock files. We're going to be comparing the 3 files [_npm-shrinkwrap.json_, _package-lock.json_, _package.json_], so you'll want to make sure you have your project folder open in Atom as well.


1\. Earlier in the worksheet, we installed the most recent version of **lodash**, so if you check the version number in _package.json_ and _package-lock.json_, they should match.  

| _package.json_ | _package-lock.json_ |
| --- | --- |
| `^4.17.4` | `4.17.4` |

2\. We're going to install an older version of **lodash** now. In your CLI type: `npm install lodash@3.10.0`  

| _package.json_ | _package-lock.json_ |
| --- | --- |
| `^3.10.0` | `3.10.0` |

3\. Let's try updating **lodash**. In your CLI, type: `npm update`

This updates within the SemVer specific version, so since _package.json_ had `^3.10.0`, this updates to `^3.10.1`, as that is the highest version available below `4.0.0`.

| _package.json_ | _package-lock.json_ |
| --- | --- |
| `^3.10.1` | `3.10.1` |

4\. Let's install the latest **lodash**, but _only_ apply it to the _package.json_. In your CLI, type: `npm install lodash@latest --no-shrinkwrap`

You should see the _package.json_ file updates with the latest version, but the _package-lock.json_ stays at the previous version.

| _package.json_ | _package-lock.json_ |
| --- | --- |
| `^4.17.4` | `3.10.1` |

Alright, let's check out _node_modules/lodash/package.json_ and see what version is listed in there. `4.17.4` Wait. I thought it was supposed to use the version in _package-lock.json_. Since we explicitly used the npm install command with a version (or a version tag like `latest` in this case), it automatically installs the new version in _node_modules_. However, it leaves the _package-lock.json_ at the `3.10.1` version.

{% hint style='danger' %}
There is currently a [bug](https://github.com/npm/npm/issues/18144) with the latest **npm** and _package-lock.json_. So we need to switch to an _npm-shrinkwrap.json_ file a little earlier in this process than we originally planned. But know that you can do the following steps with the _package-lock.json_ and have the same outcome (once the bug is fixed).
{% endhint %}

5\. Let's switch our _package-lock.json_ file to an _npm-shrinkwrap.json_ file. In your CLI, type: `npm shrinkwrap`

You should see the file that was named _package-lock.json_ in your project is now named _npm-shrinkwrap.json_.

{% hint style='info' %}
There are 2 differences between _package-lock.json_ & _npm-shrinkwrap.json_.

* The _npm-shrinkwrap.json_ has higher priority, so if both are present in your project, _npm-shrinkwrap.json_ will be used.

* The _package-lock.json_ is only meant to be used for the development of your project. If you're publishing your project as an **npm** package, _package-lock.json_ cannot be included in the publicly available files for the package. **If** you need to publish the version locks for your package, then you'll want to use _npm-shrinkwrap.json_ as it can be publicly shared. However, this is really only in cases when your package is either a background process or a utility to use in command line, like **Yeoman** or **Browserify**.
{% endhint %}

6\. Delete the _node_modules_ folder from your directory. [Yes, the whole thing.]

7\. Let's do a fresh install. In your CLI, type: `npm install`

You should still see the following versions in their respective files:

| _package.json_ | _npm-shrinkwrap.json_ |
| --- | --- |
| `^4.17.4` | `3.10.1` |

But take a look in the _npm_modules/lodash/package.json_ file & notice that the version in there matches _npm-shrinkwrap.json_ and **not** the version in _package.json_.

{% hint style='info' %}
The bug that currently exists for the _package-lock.json_ is if you delete `node_modules` & do a fresh install, `package-lock.json` is updated to the version specified in _package.json_. However, the _npm-shrinkwrap.json_ file works correctly b/c it retains the previously "locked" version.
{% endhint %}
