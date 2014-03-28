LESS
====

##Objectives

This is a really simple example of how to use basic LESS. Why do more when you can do LESS?

###Step 1: Creating, compiling and watching your LESS file
Fairly simple step, but done incorrectly and it could result in some major frustration. If your lESS isn't compiling to the right sheet, you will never see your changes!!!
1. Create your style.less file
2. Add the following to your style.less. This is just basic CSS to see the divs.
```less
.shape{
  display:inline-block;
  width:200px;
  height:200px;
  background:#ddf;
  margin:20px;
}
```
2. Compile your style .less into style.css or whatever your preference is. The only 'set' parameter is the 'lessc'.

```shell
    lessc style.less > style.css

```


