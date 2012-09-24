# Style Pages

The goal of this project is to grow into a full style guide generation app for designing in browser. This is an adaptation of the wonderful Style Guide built by [Mason Wendell](http://twitter.com/codingdesigner) for his kick ass [Survival Kit](http://github.com/canarymason/survival-kit).

## Requirements and Installation
Style pages, for the time being, require [Serve](http://get-serve.com) to run. It makes is really super easy to deal with. In addition to Serve, there are a handful of other gems you're going to need to install. The following line should install everything for you (from the command line):

```
gem install serve haml compass sass toolkit compass-normalize sassy-buttons
```

Once you have all of that install, `cd` into your fork from the command line (so something like `cd /path/to/project/stylepages`) and, in the stylepages directory, type `serve` to start the Serve webserver. You'll be able to access your Style Guide by going to `localhost:4000` from your browser.

## Usage
Pretty easy. Edit the variables inside of the `setup/*.haml` and `setup/*.scss` files to corispond to your client's needs, write your style guide in `style-guide` being sure to include all partials in the provided file, run `serve` at the stylepages root, and you're good to go! You should never really need to dive into or edit anything in the `views` directory unless you are adding new pages that don't already exist or really need to edit those that do.

Have fun!

## License
© Sam Richard and Mason Wendell.

Licensed under MIT/GLPv2 (except for Open Source projects, see their corrisponding licenses)

GPL license: http://www.gnu.org/licenses/gpl.html

MIT license: http://www.opensource.org/licenses/mit-license.php