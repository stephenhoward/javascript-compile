# Javascript::Compile

A preprocessor that minifies and allows for includes in js files

## Usage

    #!/usr/bin/env perl

    use strict;
    use warnings;

    use Javascript::Compile;

    Javascript::Compile::compile_js( '/myproject/static/js' => '/myproject/var/static/js' );

Alternatively you can have multiple input directories output to a single output directory:

    Javascript::Compile::compile_js( [ '/myproject/static/js','/myproject/other/js' ] => '/myproject/var/static/js' );

## Setup

This assumes that your source directory has a `bin` and `lib` directory in it.  It will run through all the files in `bin` and minify them.  Those files may include files from the `lib` directory like so:

    /* include bar.js */

This will tell the file to look for `/myproject/static/js/lib/bar.js` and inline it at the top of the file.

An optional third option, if set to a true value, will disable minification of the javascript output, which can be useful for debugging.
