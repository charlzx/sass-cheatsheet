### <b>SASS - Syntatically Awesome Stylesheet</b>
Sass is a CSS pre-processor. It allows css to act more like an actual programming language, and it's more efficient.
Browsers doesn't read Sass directly, it has to be compiled down to regular css, using a Sass compiler.

### Installing Sass globally using npm
    sudo npm i -g sass

### Watching Sass in the workspace
    sass --watch scss/style.scss  css/style.css
###
    where,
    scss/style.scss ⇋ is the location of the sass file to be compiled.
    css/style.css ⇋ is the location of the css file where the sass file while be compiled into.

### Extensions
sass has 2 file extensions that can be used based on preference.

### .scss
    the scss extension is more backward compatible with regular CSS.
    it supports the use of curly braces.
### .sass
    the scss extension doesn't support curly braces.
    instead, it makes use of indentation.


### Syntax
    sass variables are pre-fixed with the "$" sign.

### Nesting
sass also supports nesting, unlike regular css.
child selectors can be nested in the parent selector.
<br>
e.g.

    nav {
        ul {
            margin: 0;
            padding: 0;
        }
        li {
            display: inline-block;
        }
        a {
            display: block;
            padding: 6px 12px;
            text-decoration: none;
        }
    }



### adding a partial file to the main sass file;
<b>@import 'config';</b>
i.e if partial file is _config.scss
<br>
or
<br>
<b>@import 'utilities';</b>
i.e if partial file is _utilities.scss

<b>p.s.</b> partial files always start with the symbol "_" but when it is imported, the symbol and file extension is omitted.


### creating shared styles;
    shared styles are created using the "%" symbol as the pre-fix.
to add the created shared style in the a selector, use;
<br>
<b>@extend %btn;</b>
i.e if shared style is %btn


### functions;
sass supports the use of functions, just like any programming language. here is a sample:;

    @function set-text-color($color){
        @if(lightness($color) > 70 ) {
            @return rgb(51, 51, 51);
        }
        @else {
            @return #fff;
        }
    }

to call the function in the stylesheet,

    a {
        color: set-text-color($primary-color);
    }
where, <b>$primary-color</b> is the color i want to use.


### mixins;
here, is an example of a mixin.

    @mixin set-background($color) {
        background-color: $color;
        color: set-text-color($color);

to call the mixin in the stylesheet,

    body {
        @include set-background($primary-color);
    }
where, <b>$primary-color</b> is the color i want to use.
<br>
to use the mixin, <b>@include</b> is used to import the mixin into the stylesheet.


### loops;
sass, supports to use of loops.
loops in sass is similar to javascript loops.
here is a snippet
   
    $spaceamounts: (1,2,3,4,5,6); 
<!-- this is  the variable, to be looped through -->

    @each $space in $spaceamounts {
        .m-#{$space} {
            margin: #{$space}rem;
        }
        .my-#{$space} {
            margin: #{$space}rem 0;
        }
        .mx-#{$space} {
            margin: 0 #{$space}rem;
        }
        .fs-#{$space} {
            font-size: #{$space * 8}px;
        }
    }
###
    loops are ideal for large projects, as the classes can be used throughout the code.
