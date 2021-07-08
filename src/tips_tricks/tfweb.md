# TFWeb tool

## whats new

- uses docsify, which means all plugins from docsify are back
- all names of .md & .jpeg/.png files need to be unique
- names will be rewritten to lowercase & snakecase
- links & images only need to refer to the shortname e.g. ```![](img/bcdb.png)``` is good enough

## Markdown / Docsify Tricks

### tabs

https://jhildenbiddle.github.io/docsify-tabs/#/?id=usage

### markdown 

please read

https://jhildenbiddle.github.io/docsify-themeable/#/markdown

### copy code

https://github.com/jperasmus/docsify-copy-code/blob/master/README.md

### resizing

```
![logo](https://docsify.js.org/_media/icon.svg ':size=WIDTHxHEIGHT')
![logo](https://docsify.js.org/_media/icon.svg ':size=50x100')
![logo](https://docsify.js.org/_media/icon.svg ':size=100')

<!-- Support percentage -->

![logo](https://docsify.js.org/_media/icon.svg ':size=10%')

```

### links

```
[link](tfweb)
[link](threefold:grid_why)
```

### remote include

```
[remoteMarkdownUrl](https://raw.githubusercontent.com/Threefoldfoundation/projects_website/master/README.md)
```

the name in [] need to be like above, and use the raw representation of the content