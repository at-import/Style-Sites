# Style Sites

The goal of this project is to grow into a full style guide generation app for designing in browser. This is an adaptation of the wonderful Style Guide built by [Mason Wendell](http://twitter.com/codingdesigner) for his kick ass [Survival Kit](http://github.com/canarymason/survival-kit).

## Requirements and Installation
Style Sites run through [Serve](http://get-serve.com). In addition to Serve, there are a handful of other gems you're going to need to install. The following line should install everything for you (from the command line):

```bash
(sudo) gem install serve haml compass sass bundler toolkit compass-normalize sassy-buttons
```

I also highly suggest investing in either [LiveReload](http://livereload.com) or similar in order to see your site update when you save your files. This makes designing in browser much much easier. LiveReload will automatically do a reload of your pages on file save, saving you from needing to switch to your browser and reload the page manually.

## Starting Your Server

After you've got everything installed, you are going to need to start the server to see the website from the terminal. Simply `cd` to your project, something like `cd /path/to/Style-Sites` and then run the following:

```bash
serve _server
```

On your first run, you may get an error saying that you need to run `bundle install`. If you do, run `bundle install` from inside the `_server` folder, but that is the last you should need to dive into the `_server` folder.

## Once Codebase, Multiple Clients

The best way to work with Style Sites is to have a branch or separate download for each of your clients. I prefer the branching method as it allows me to version the style changes and keep an easy log of everything that's changed. There are two ways you can do this; if you're uncomfortable or new to Git, I'd suggest downloading, installing, and using the official [GitHub for Mac](http://mac.github.com) client to handle your Git repositories and branches. Otherwise, use the command line! There's lots of [documentation on branching with Git], so read up if you're unfamiliar with the concept or are new to Git.

## Setting Up Your Style Site

Once you have everything in place and you have your server running, setting up your style site is very easy. Inside the `setup` directory, you will find the following files, in order of importance:

* client.haml
* webfonts.haml
* client-styleguide.rb
* javascript.haml
* development.haml
* _page-setup.scss
* sections.haml
* variables.haml

You will also find two directories, the `images` directory and the `js` directory. You can add and reference the images through the exposed variables and through your Sass. If you want to add any non-standard JavaScript to the page, you can do so using the `@customJS` variable inside of the `js.haml` file.

### client.haml

This is where all of the basic information about you and your client goes. Fairly simple, replace "Client Name" in `@clientName` with your client's name, if you have a logo, put it in the `images` folder and make sure the path is correct (otherwise, set it to `false`), and put a version in! Also, be sure to replace "Author Name" in `@author` with your name!

### webfonts.haml

One of the most awesome things about designing in browser is being able to use real web fonts! Web fonts rock! There are two easy ways of using web fonts with Style Sites, the first is with [Typekit](https://typekit.com). Simply grab your Typekit Kid ID (at the bottom of the "Embed Code" popup) and replace the `false` in `@typekitID` with your kit ID, wrapped in "double quotes". Be sure to include `localhost` in the domains in your Kit Settings. If you'd prefer to use [Google Fonts](https://www.google.com/webfonts), simply pick out your fonts, and when you're ready to use, click on the Javascript tab in Step 3, and copy what's inside the [brackets] on line 3. For instance, if you had the following Goole Fonts code from the Javascript tab in Step 3:

`<script type="text/javascript">
  WebFontConfig = {
    google: { families: [ 'Offside::latin' ] }
  };
  (function() {
    var wf = document.createElement('script');
    wf.src = ('https:' == document.location.protocol ? 'https' : 'http') +
      '://ajax.googleapis.com/ajax/libs/webfont/1/webfont.js';
    wf.type = 'text/javascript';
    wf.async = 'true';
    var s = document.getElementsByTagName('script')[0];
    s.parentNode.insertBefore(wf, s);
  })(); </script>
  `
  
You would replace `false` in `@googleFonts` with `"'Offside::latin'"`. Again, be sure to wrap the fonts in "double quotes".

### client-styleguide.rb

This file is used for when you're ready to turn your built style guide into a Compass extension, this tells Compass the name of your Compass extension  as well as what other gems are required. You generally won't need to touch anything in this file except for changing the name of the file to the actual name of your client, and changing the two instances of Client Styleguide, one `client-styleguide` on line 16 and one `Client_Styleguide` on line 24. If you create new versions of your style guide, be sure to update Version and Date accordingly before building a new gem.

### javascript.haml

All of your JavaScript needs! This file will allow you to quickly and easily add custom JavaScript to your site (beyond the default [Modernizr](http://modernizr.com/) build). By filling out one of the JavaScript Library variables, you'll get that full Library pulled in. If you'd like to custom JavaScript beyond that, the `@customJS` variable will allow you to add in any JavaScript you'd like, just throw them in the `js` folder. By default, no libraries are on, but we're pulling in [Chibi](https://github.com/kylebarrow/chibi) and [Hammer.js](http://eightmedia.github.com/hammer.js/). If you want to remove all custom JS, set `@customJS` to `false`. If you want to use a full JavaScript Library, be sure to remove Chibi.

### development.haml

There is currently one variable in here. Toggle `@LiveReload` to `true` to automatically add in the LiveReload script. This is especially useful when testing in browsers that don't have LiveReload extensions (such as the iOS emulator or Internet Explorer)

### _page-setup.scss

This file contains a handful of variables to set up the skeleton for the style site itself. Change them as you see fit!

### sections.haml

This section allows you to choose what sections of you'd like in your Style Site. You can rename, redirect, or create new sections with ease. Creating a new section is easy, simply place the haml file into the `custom` folder; there are two example folders in there, a Drupal UI and a General UI folder with corresponding haml files that you can use as guidance. Once you've created your custom haml files, add them to the `@sections` variable.

### variables.haml

This file currently contains nothing and does nothing. This file may be going away in future releases.

## Your Style Guide

Your Style Guide is the driving force behind the Style Site! Use the Common Markup, Common HTML5, Typography, and UI Pattern pages to help you theme out your style guide, using as least specific selectors as possible. Included is a `global` folder containing the basic base items for sharing across the Colour Guide and Style Tile.

Inside your `global/_colours.scss` file are a handful of sample colours using [Toolkit's Colour Stack](https://github.com/snugug/toolkit#colour-stacks) functions to give you an idea as to how to use them in your Style Guide. Inside of `global/_base.scss` you'll see . In the main `_style-guide.scss` there is a little Sass for loop to colour your H1-H6 tags with the black shades that come by default. Feel free to remove them, and change the colours!

Remember! Any and all CSS that you put into files and folders in the `style-guide` folder *will be available in the generated Compass Extension!* Because of this, it's highly suggested that your styles be as least specific as possible and as concise as possible!

## Your Colour Guide

Your Colour Guide is designed to be built based on colour stacks you've designated in your Style Guide. Inside `_color-guide.scss` on Line 13 you'll see a Sass mixing `generate-colour-guide` with a list of variables that match up to the colours inside of `style-guide/global/_colours.scss`. The list goes in the order you want them to appear. In `colours.haml`, you'll see two variables, `@colours` which is a list of the names of your colour variables, in order they get used in `generate-colour-guide`, and `@colourShades` which is the number of total colours in a colour stack. The default being used, `tint-stack`, adds five colours to the base colour for a total of 6 shades per colour.

Adding a new colour to your colour guide is a three step process.

1. Add the variable and its corresponding colour stack to `style-guide/global/_colours.scss`. For this example, we're going to add `$badass: tint-stack(#b4d455);`
2. Add the variable in place in the mixing in `color-guide/_colour-guide.scss`. We're going to add it at the end, so using the example that comes with Style Sites, our `generate-colour-guide` mixin will now look like the following: `@include generate-colour-guide($black, $red, $orange, $yellow, $green, $blue, $purple, $badass);`
3. Add the variable name to the `@colours` variable in `color-guide/colours.haml`. Using the example that comes with Style Sites, our `@colours` variable will now look like the following: `@colours = ['black', 'red', 'orange', 'yellow', 'green', 'blue', 'purple', 'badass']`

## Your Style Tile

If you've built out your Style Guide before your Style Tile, there isn't much that really should go into the `_style-tile.scss` file. That being said, any styles you need to make the style tile look correct should go in here. It's important to note that anything you put in this file will not be available in your final Compass Extension, so keep that in mind. On Line 13, there is a `possible-colours` mixin that will deal with colouring the possible colours squares. The number of Possible Colours is controlled inside `tile.haml`. Inside `tile.haml` is also an array of Possible Patterns pointing toward images, either from the web or inside the `images` directory. You can create demo buttons on the Style Tile by defining classes you'd like the button to have with buttons with more than one class being wrapped in [brackets]. These buttons will also show up on the UI Patterns page, if you have that section enabled. There is also a place for you to put the list of words that inspired this Style Tile. For more on Style Tiles, see the [Style Tiles site](http://styletil.es/).

## Creating your Compass Extension

Once you're done with your Style Site, it's drop dead easy to turn it into a Compass Extension to be used on any project you wish! 

1. Rename `client-styleguide.gemspec` the same name you used for `setup/client-styleguide.rb`
2. Open `client-styleguide.gemspec`
3. Make sure that `require '/.setup/client-styleguide.rb` is changed to your renamed `client-styleguide.rb`
4. Make sure that `Client_Styleguide` is changed to what you used in `client-styleguide` for `s.version` and `s.date`
5. Change the value of `s.name` to match the name of the file
6. Edit `s.description`, `s.summary`, `s.authors`, `s.email`, and `s.homepage` respectively.

Once you're done with the edits, save, and in your command line, run `gem build client-styleguide.gemspec` (using the name of your renamed gemspec) and you've got a working Compass extension! This will create a gem called `client-styleguide-1.0.gem` (the 1.0 is the version number from `setup/client-styleguide.rb`, and the `client-styleguide` will actually be the name you renamed everything).

## HAVE FUN!

## License
© Sam Richard and Mason Wendell.

Original code licensed under MIT/GLPv2
Open Source projects used within this project retain their original licenses.

GPL license: http://www.gnu.org/licenses/gpl.html

MIT license: http://www.opensource.org/licenses/mit-license.php
