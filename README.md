#Webikon Guidelines

Writing good and readable code when developing WP solutions in a team is pretty hard. 
Every one of us has his own style of writing code, uses different namespaces or follows different standards.
But in a team, we need to work together and we need to have our code consistent and understandable by everybody.  


##CSS
- keep specificity as low as possible
- DON'T use ids!
- DON'T use important! unless it is really neccessary: ```.hidden { display: none !important; }```

###Syntax and formatting
With proper syntax and formatting code will look nicer and more clean.
Some basic rules are:
 - one tab indent
 - css is written in multiple lines
 - empty line after ruleset
 - use spaces

SCSS linter would warn us about those.
For SublimeText: https://packagecontrol.io/packages/SublimeLinter-contrib-scss-lint

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

#### Nesting
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

###Naming
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

### CSS Attributes
Divide into two groups:
- how it is positioned: position, float, z-index,...
- how it looks: font, border, color, background-color,...
