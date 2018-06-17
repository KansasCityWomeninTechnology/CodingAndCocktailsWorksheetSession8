### Part 1: Create a project folder {#part-1-create-a-project-folder}

When you’re starting from scratch, an empty project is simply an empty folder. You could do that visually (using your file explorer) but let’s do it on the command line.

1.  Navigate to your _CodingAndCocktails_ folder in your CLI. Type: `cd [yourHomeDirectory]/CodingAndCocktails`

  {% hint style='tip' %}
  #### Command line woes?
  - Your home directory is:
    - Mac: `/users/<yourUsername>`
    - Windows: `C:/Users/<yourUsername>`
  - Command to change folders: `cd <folderToGoTo>`
  - Command to make a folder: `mkdir <newFolder>`
  - Most command line applications are not case-sensitive, but a few of them are!

  Revisit the command line worksheet from March:
  [bit.ly/CnCMarWork](http://bit.ly/CnCMarWork)
  {% endhint %}

2.  Make a new folder called **packagesproject**. Type: `mkdir packagesproject`

  {% hint style='danger' %}
  If you joined us last year and already have a _packagesproject_ folder. Delete or rename the old folder & create a new one for tonight's project.
  {% endhint %}

3.  Move into that new folder: `cd packagesproject`

  {% hint style='tip' %}
  #### Command line woes?

  If you start typing the name of a folder or file, hit tab and it will autocomplete
  {% endhint %}

4.  Open the Atom text editor from here. Type: `atom .`

  <!--sec data-title="Chromebooks Only: Cloud9 Instructions" data-id="section0" data-show=true data-collapse=true ces-->
  The Cloud9 workspace includes a built-in text editor that you'll be using instead of Atom. In order to open a file in Cloud9, you'll double-click on the file name in the left sidebar.
  <!--endsec-->

  {% hint style='danger' %}
  #### Command not found
  If Atom doesn't open (but you know it's installed), your system probably doesn't recognize the `atom` command.

  You can configure your system to recognize the command (ask a mentor for help) or you can follow these steps to open it manually:

  1. From your applications or start menu, open Atom
  2. In Atom: **File** >> **Open...** (Mac) or **Open Folder...** (Windows)
  3. Open the _packagesproject_ folder
  4. Click the **Open** button
  {% endhint %}
