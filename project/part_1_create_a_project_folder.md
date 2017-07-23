### Part 1: Create a project folder {#part-1-create-a-project-folder}

When you’re starting from scratch, an empty project is simply an empty folder. You could do that visually (using your file explorer) but let’s do it on the command line.

{% hint style='info' %}
#### Command line woes?
Revisit the command line worksheet from March:
[bit.ly/CnCMarWork](http://bit.ly/CnCMarWork)
{% endhint %}

1.  Navigate to your _CodingAndCocktails_ folder. Type: `cd [yourHomeDirectory]/CodingAndCocktails`

  {% hint style='tip' %}
  #### Command line woes?
  - Your home directory is:
    - Mac: `/users/<yourUsername>`
    - Windows: `C:/Users/<yourUsername>`
  - Command to change folders: `cd <folderToGoTo>`
  - Command to make a folder: `mkdir <newFolder>`
  - Most command line applications are not case-sensitive, but a few of them are!
  {% endhint %}

2.  Make a new folder called **packagesproject**. Type:: `mkdir packagesproject`
3.  Move into that new folder: `cd packagesproject`

  {% hint style='tip' %}
  #### Command line woes?
  - If you start typing the name of a folder or file, hit tab and it will autocomplete
  {% endhint %}

4.  Open the Atom text editor from here. Type: `atom .`

  {% hint style='danger' %}
  #### Command not found
  If Atom doesn't open (but you know it's installed), your system probably doesn't recognize the `atom` command.

  You can configure your system to recognize the command (ask a mentor for help) or you can follow these steps to open it manually:

  1. From your applications or start menu, open Atom
  2. In Atom: **File** >> **Open Folder...**
  3. Open the _packagesproject_ folder
  4. Click the **Open** button
  {% endhint %}
