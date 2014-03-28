LESS
====

##Objectives

This is a really simple example of how to use basic LESS. Why do more when you can do LESS?

###Step 1: Creating, compiling and watching your LESS file
Fairly simple step, but done incorrectly and it could result in some major frustration. If your lESS isn't compiling to the right sheet, you will never see your changes!!!
* If you haven't already, go ahead and install the LESS module:

```shell
npm install less -g
```
* Create your style.less file
* Add the following to your style.less. This is just basic CSS to see the divs.
```less
.shape{
  display:inline-block;
  width:200px;
  height:200px;
  background:#ddf;
  margin:20px;
}
```
* Compile your style.less into style.css or whatever your preference is. The only 'set' parameter is the 'lessc'.

```shell
lessc style.less > style.css
```

###Step 2: Variables
Static CSS isn't very modular or flexible. We are going to start using LESS to help keep our CSS DRY'er and cleaner.
* Add in 3 different variables for colors. Remember that variables in LESS begin with @.
* Variables are just constants, so replacing a hexadecimal number with a variable won't do you any good. You would still have to change where the variable is referenced to any new color or variable you wanted to use. Add a new variable @default-theme to create a variable to control your theme. Now, when you need to change a color or styling, you just have to change it in the one place.

```less
@blue: #dff;
@default-theme: @blue;

.shape{
  display:inline-block;
  width:200px;
  height:200px;
  background:@default-theme;
  margin:20px;
```

###Step 3: Mixins
Mixins provide an easy way to 'mixin' css classes into other css. Mixins in LESS start with a period(.).
* Create a mixin that will change the border radius of the shapes and include all the prefixes(-webkit, -moz).
* Create a mixin called @rounded-shape that takes a radius as a parameter and set that radius to a default value. The rounded shape mixin should return the border-radius declaration with the radius parameter.

```less
.rounded-shape(@radius: 30px){
-webkit-border-radius:@radius;
       -moz-border-radius:@radius;
            border-radius:@radius;
}
```
* Now create 2 other mixins that include the rounded shape. One mixin should be for a circle and the other should be for a square with rounded corners. This is going to demonstrate how a mixin can be included in another mixin to provide more modularity. Every time you want to create a circle, you can call the circle mixin and anytime you need a square with rounded corners, you can call the rounded square mixin. Now you should have 3 mixins that do a ton of logic in very few lines. Pretty Cool!

```less
.circle{
    .rounded-shape(999px);
}

.rounded-square(@radius: 30px){
    .rounded-shape(@radius);
}
```

* Don't forget to include your new mixin in the selector declaration!

```less
#shape1{
    .circle;
}

#shape2{
    .rounded-square;
}

#shape3{
    .rounded-square(30px);
}
```

###Step 4: Operations, functions, and nesting
Sometimes we want something to be a different pixel size or different color without really knowing the value we want to use. On a hover effect, we may just want the color to be darker or lighter or we may want the border to get wider or more narrow. This is where operations come in handy. LESS even has built in functions that can handle these operations for you.

* Create a border color variable that is a different color than the background color. You can use a LESS color function or you could use an operation to create the color.


```less
@border-color: @default-theme - #222;

//or

@border-color: darken(@default-theme, 20%);
```
Nesting is a great way to use less code(no pun intended). At times you may need to chain selectors to capture a particular DOM element. Long chains in CSS may be hard to read and understand. With nesting, you can nest selectors in parent selectors. This creates a more visually appealing chaining and easier to read css.

* Create a hover effect for one of your elements. Nested selectors can access the parent element with the &.

```less
.shape{
    &:hover{
        background: @light-red;
    }
}
```






