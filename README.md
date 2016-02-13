# Learning-SASS
Self study into SASS and HTML5 through creating a single page website.

Completed! :D

https://rawgit.com/carleneconner/Learning-SASS/master/index.html


### Setting Up SASS From the Command Line

In order to install SASS, I first needed to download and install Ruby.
I was then able to install SASS from the Command Line with:

                    
    gem install sass
                    
                

### Creating an Initial Project

Using Jet Brains' WebStorm IDE, I created a new empty project. Added this index.html page, a folder for Stylesheets and in it a main.scss.

From the command line I am able to run the preprocessor manually on individual .scss files to convert them into usable .css 
files. Or I can choose to watch one or more files or folders containing .scss files. This would automatically pre-process 
valid .scss files whenever a change has been made.

However, once SASS has been installed, there is a handy feature in WebStorm that automatically detects .scss files and asks if 
you would like them watched.

### Partials and Imports

I created a main.scss. This is where most of the default rules will be specified. I have created 3 partials because this site 
may be viewed on various devices. One specifies the rules to be applied when viewing this site on a phone, one for a tablet and one for a desktop. In the main.scss I import each of these partials in turn, surrounding them in conditional statements so they are only applied when needed e.g.

                    
    @media only screen and (min-width: 600px) {
        @import "tablet";
                    
                

### Variables

The use of variables allows for increased maintainability. A value that I may use more than once in a typical CSS document 
now, only needs to be defined once. e.g.

                    
    $main-font: "Helvetica Neue, Helvetica, Arial, sans-serif";
                    
                

### Nesting

With nesting there is no need to repeat element names, that apply to more than one thing.

                    
    nav {
        background: $alt1-colour;

        ul li {
            list-style-type: none;
            width: 50%;
            float: left;
        }

        a {
            display:block;
            background:$alt2-colour;
        }
        a:hover {
            color:white;
        }
    }
                    
                

The SCSS code above generates the following CSS, Note 'nav' has been included where it is needed:

                    
    nav {
        background: #18cdca;
    }

    nav ul li {
        list-style-type: none;
        width: 50%;
        float: left;
    }

    nav a {
        display: block;
        background: #4f80e1;
    }
    nav a:hover {
        color: white;
    }
                    
                

### Mixins

Mixins are similar to functions in that, you are abe to pass in values.

                    
    @mixin border-radius ($radius) {
        -webkit-border-radius: $radius;
        -moz-border-radius: $radius;
        -ms-border-radius: $radius;
        border-radius: $radius;
    }
                    
                

The above mixin could be called with:

                    
    .main_image {
        border:1.5px solid grey;
        @include border-radius(10px);
    }
                    
                

### Maths Operators

Basic arithmetic can be used to help work out the appropriate figures required. In my example I want the element to take up 
eight twelfth's of the available space, and also take into account some room for margins.

                    
    $width: 8 / 12 * 100%;
    width: $width - 4%;
                    
                

### Extend or Inheritance

If you wish two or more elements to share some of the same properties, you can use extend. In my example .nav_link_top will 
contain all the CSS rules currently defined in .nav_link_section, by using @extend. I can then customise .nav_link_top further,
for instance with a greater font weight.

                        
        .nav_link_section {
            font-size: .7em;
            margin:2px;
            text-decoration:none;
        }

        .nav_link_top {
            @extend .nav_link_section;
            font-weight: 600;
        }
                        
                    

