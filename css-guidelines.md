#CSS Guidelines

- keep specificity as low as possible
- DON'T use ids!
- DON'T use important! unless it is really neccessary: ```.hidden { display: none !important; }```

##Syntax and formatting
With proper syntax and formatting code will look nicer and more clean.
Some basic rules are:
 - one tab indent
 - css is written in multiple lines
 - empty line after ruleset
 - use spaces

SCSS linter would warn us about those. <br />
For SublimeText: https://packagecontrol.io/packages/SublimeLinter-contrib-scss-lint <br />
Place [.scss-lint.yml](.scss-lint.yml) in the root of project or in the [Home directory](https://en.wikipedia.org/wiki/Home_directory#Default_home_directory_per_operating_system)

Example:

```
// bad
.foo,.foo--bar,.baz{
    display:block;
    background-color:green; color:red;
}
.foo {
    color: red;
    &:hover {
        color: blue;
    }
}
.baz {
    color: green;
}
```

```
// good
.foo, 
.foo--bar,
.baz {
    display: block;
    background-color: green;
    color: red;
}

// use of empty line
.foo {
    color: red;

    &:hover {
        color: blue;
    }
}

.baz {
    color: green;
}

```

###Nesting
- max 3 levels, but 1 is ideal
- use primarily to simplify typing of component classes

```
.component-with-longer-name {
    &-element {
    }

    &-header {
    }
}
```

##Naming
We are using component based class naming, similar to BEM.
Use of this method will ensure, that specificity of our CSS would be low.
 
```
.component-descendant-descendant {} // basic structure
.component--modifier {} // for different variantions
.component.is-state {} // for different states
```

```
// bad
.nav {
    .item {
        a {
            //...
        }
    }

    .featured-item {

    }
}

.accordion {
    .content {

    }

    .content.hidden {

    }
}
```

```
// good
.nav {}
.nav-item {}
.nav-item--featured {}
.nav-item-link {}

.accordion {}
.accordion-content {}
.accordion-content.is-hidden {}

```

##CSS Attributes
Divide into two groups:
- how it is positioned: position, float, z-index,...
- how it looks: font, border, color, background-color,...


This guidelines were influenced by many articles and discussions on the web. 
Another really good inspirations were [10up's Best Practices](https://10up.github.io/Engineering-Best-Practices/css/)
and [Harry Robert's CSS Guidelines](http://cssguidelin.es/)