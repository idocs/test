---
title       : Introduction
subtitle    : Slidify Workshop
author      : Ramnath Vaidyanathan
hitheme     : solarized_light 
mode        : selfcontained # {standalone, draft}
assets:
  js:
    - "http://ajax.googleapis.com/ajax/libs/jqueryui/1.10.3/jquery-ui.min.js"
    - "http://bartaz.github.io/sandbox.js/jquery.highlight.js"
  css: "http://fonts.googleapis.com/css?family=Crimson+Text"
---

## Publishing to Github

1. Add Local Repository
2. Commit Changes
3. Publish!


```r
knitr::knit_hooks$set(document = function(doc) {
    gsub("```", "```", doc)
})
```



--- .centrepre &draggable


## My Report

    Today I built a model
    
    ```{r}
    fit = lm(dist ~ speed, data = cars)
    ```
    
    and I got the slope
    
    
    ```{r dist-speed, fig.width=5, fig.height=4}
    plot(cars)
    abline(fit)
    ```
    

*** #draggable1 .right

title

--- &draggable

## Draggable

*** #draggable2

__Direction__: What is the direction of the relationship?


--- .segue .dark .nobackground

## Deck


--- &callout #step3a .centrepre


	---
	title: Slidify
	author: Ramnath Vaidyanathan
	framework: io2012
	---
	## Get Started
	
	Slidify is easy to use, only three rules!
	
	1. Write content using R Markdown
	3. Add properties using YAML
	4. Separate slides using `---`
	
	---
	## Example Slide
	
	Let us create a __scatterplot__
	
	```{r}
	require(ggplot2)
	qplot(wt, mpg, data = mtcars)
	```


*** #draggable5 .left

Properties

--- &callout #step3b .centrepre


	---
	title: Slidify
	author: Ramnath Vaidyanathan
	framework: io2012
	---
	## Get Started
	
	Slidify is easy to use, only three rules!
	
	1. Write content using R Markdown
	3. Add properties using YAML
	4. Separate slides using `---`
	
	---
	## Example Slide
	
	Let us create a __scatterplot__
	
	```{r}
	require(ggplot2)
	qplot(wt, mpg, data = mtcars)
	```


*** #draggable6 .left

Slide

--- &callout #step3c .centrepre


	---
	title: Slidify
	author: Ramnath Vaidyanathan
	framework: io2012
	---
	## Get Started
	
	Slidify is easy to use, only three rules!
	
	1. Write content using R Markdown
	3. Add properties using YAML
	4. Separate slides using `---`
	
	---
	## Example Slide
	
	Let us create a __scatterplot__
	
	```{r}
	require(ggplot2)
	qplot(wt, mpg, data = mtcars)
	```


*** #draggable7 .left

Separator

--- &callout #step3d .centrepre


	---
	title: Slidify
	author: Ramnath Vaidyanathan
	framework: io2012
	---
	## Get Started
	
	Slidify is easy to use, only three rules!
	
	1. Write content using R Markdown
	3. Add properties using YAML
	4. Separate slides using `---`
	
	---
	## Example Slide
	
	Let us create a __scatterplot__
	
	```{r}
	require(ggplot2)
	qplot(wt, mpg, data = mtcars)
	```


*** #draggable8 .right

Markdown


--- &callout #step3e .centrepre


	---
	title: Slidify
	author: Ramnath Vaidyanathan
	framework: io2012
	---
	## Get Started
	
	Slidify is easy to use, only three rules!
	
	1. Write content using R Markdown
	3. Add properties using YAML
	4. Separate slides using `---`
	
	---
	## Example Slide
	
	Let us create a __scatterplot__
	
	```{r}
	require(ggplot2)
	qplot(wt, mpg, data = mtcars)
	```


*** #draggable9 .right

Code Chunk

--- .segue .dark .nobackground

## Slide

--- .centrepre



	--- {class: [class1, class2], id: id}
	
	## Title
	
	Some content
	
	*** {name: block1, class: class3}
	
	## Block1 Title
	
	Some contents of block 1
	
	*** {bg: green}
	
	## Block2 Title
	
	Some contents of block 2



--- {id: step1a, tpl: callout, class: 'centrepre'}

```no-highlight

 --- {class: [class1, class2], id: id}
 
 ## Title
 
 Some content
 
 *** {name: block1, class: class3}
 
 ## Block1 Title
 
 Some contents of block 1
 
 *** {bg: green}
 
 ## Block2 Title
 
 Some contents of block 2


```

*** .right

Properties

*** =pnotes

### Properties

Slide properties are key-value pairs that are passed to the layout. You can specify class, id and bg and style the slide, either by using built in classes, or specifying additional css.

    --- {class: [class1, class2], id: id}

You can also use symbolic css style prefixes for frequently used properties. For instance, a dot indicates class, a hash refers to id and an ampersand identifies a layout.

    --- .class1 .class2 #id


--- .centrepre #step1b &callout

```no-highlight

 --- {class: [class1, class2], id: id}
 
 ## Title
 
 Some content
 
 *** {name: block1, class: class3}
 
 ## Block1 Title
 
 Some contents of block 1
 
 *** {bg: green}
 
 ## Block2 Title
 
 Some contents of block 2


```

*** .left

Title

--- .centrepre #step1c &callout

```no-highlight

 --- {class: [class1, class2], id: id}
 
 ## Title
 
 Some content
 
 *** {name: block1, class: class3}
 
 ## Block1 Title
 
 Some contents of block 1
 
 *** {bg: green}
 
 ## Block2 Title
 
 Some contents of block 2


```

*** .left

Content

--- .centrepre #step1d &callout

```no-highlight

 --- {class: [class1, class2], id: id}
 
 ## Title
 
 Some content
 
 *** {name: block1, class: class3}
 
 ## Block1 Title
 
 Some contents of block 1
 
 *** {bg: green}
 
 ## Block2 Title
 
 Some contents of block 2


```

*** .left

Blocks

*** =pnotes

## Blocks

Blocks are slides nested within a slide, identified by three stars. Just like a slide, they can contain  properties, title and content. 

There are two types of blocks - named and unnamed. A block can be named by specifying the property `{name: block1}` (or using the symbolic shortcut `{=block1}`). 

A block with the name `block1` can be accessed in a slide layout as `slide.block1`. The title and content of this block can be accessed as `slide.block1.title` and `slide.block1.content`. Unnamed blocks are aggregated into the namespace `slide.blocks`. 

--- .segue .dark .nobackground

## Inheritance

--- .centrepre .RAW &vcenter .bigger

```
<slide class="{{ slide.class }}">
  <hgroup>
    {{{ slide.header }}}
  </hgroup>
  <article>
    {{{ slide.content }}}  
   
      
   
  </article>
</slide>
```

*** =pnotes

Consider the following layout. Suppose, you want some slides in your deck to display a footer with a logo.

--- .centrepre .RAW &vcenter .bigger

```
<slide class="{{ slide.class }}">
  <hgroup>
    {{{ slide.header }}}
  </hgroup>
  <article>
    {{{ slide.content }}}  
   <footer class = 'logo'>
      <img src = 'path/to/logo'></img>
   </footer>
  </article>
</slide>
```

*** =pnotes

One way is to create a new slide layout adding the custom footer after `{{{ slide.content }}}`, saving it to `assets/layouts` and using it as a custom layout.

However, this is not efficient for two reasons. 

- It is not DRY and repeats code unnecessarily. 
- When the default slide layout is modified, you need to manually modify the custom layout to ensure that layouts are in sync. This could happen when you decide to use a different HTML5 slide framework, which has a different markup for slides. This is where layout inheritance comes to play.

Note that while defining your custom slide layout, you are essentially replacing the `{{{ slide.content }}}` placeholder in the slide layout by `{{{ slide.content }}}` + footer. Slidify provides a mechanism, where layouts can inherit from a parent layout, thereby simplifying the template considerably and keeping thing DRY.

--- .centrepre .RAW &vcenter .bigger

    ---
    layout: slide
    ---    
     
     
        {{{ slide.content }}}  
       <footer class = 'logo'>
          <img src = 'path/to/logo'></img>
       </footer>
      </article>
    </slide>

*** =pnotes

This is the modified layout for this use-case using inheritance. The YAML front matter indicates that this template inherits from slide, which is the default slide layout.

--- .segue .dark .nobackground

## Journey of a Slide

--- &vcenter .centrepre

    --- {class: class1, bg: yellow}
    
    ## Slide Title
    
    Slide Contents
    
    *** =pnotes
    
    Some notes


--- &vcenter .centrepre

    $html
    [1] "<h2>Slide Title</h2>\n\n<p>Slide Contents</p>\n"
    
    $header
    [1] "<h2>Slide Title</h2>"
    
    $level
    [1] "2"
    
    $title
    [1] "Slide Title"
    
    $content
    [1] "<p>Slide Contents</p>\n"
    
    $class
    [1] "class1"
    
    $bg
    [1] "yellow"
    

--- &vcenter .centrepre .RAW #myhtml

```html
<slide class="{{ slide.class }}" style="background:{{ slide.bg }};">
  {{# slide.header }}
  <hgroup>
    {{{ slide.header}}}
  </hgroup>
  {{/ slide.header }}
  <article>
    {{{ slide.content }}}
  </article>
  <!-- Presenter Notes -->
  {{# slide.pnotes }}
  <aside class="note" id="{{ id }}">
    <section>
      {{{ html }}}
    </section>
  </aside>
  {{/ slide.pnotes }}
</slide>
```

<style>#myhtml pre{width: 95%}</style>

--- &vcenter .centrepre .RAW #myhtml2

```no-highlight
<slide class="{{ slide.class }}" style="background:{{ slide.bg }};">
  {{# slide.header }}
  <hgroup>
    {{{ slide.header}}}
  </hgroup>
  {{/ slide.header }}
  <article>
    {{{ slide.content }}}
  </article>
  <!-- Presenter Notes -->
  {{# slide.pnotes }}
  <aside class="note" id="{{ id }}">
    <section>
      {{{ html }}}
    </section>
  </aside>
  {{/ slide.pnotes }}
</slide>
```

<style>#myhtml2 pre{width: 95%}</style>

--- .dark .nobackground .segue

## Code Chunks

--- .centrepre &callout #chunk1

    ```{r example, fig.width = 6, comment = NA}
    x <- 1+1
    rnorm(5)
    ```
    
*** .left #markup build:true

Markup

*** .top #label build:true

Label


*** .top #options build:true

Options

*** .bottom #code1 build:true

Code

--- .centrepre &callout #chunk2



	```{r example, fig.width = 6, comment = NA}
	x <- 1+1
	rnorm(5)
	```



    
*** .left #markup

Markup

--- .dark .quote .nobackground

<q>The overriding design goal for Markdown’s formatting syntax is to make it as readable as possible. The idea is that a Markdown-formatted document should be publishable as-is, as plain text, without looking like it’s been marked up with tags or formatting instructions.</q>

--- .segue .dark .nobackground

## Frameworks

--- .centrepre &callout #impress-example .wrap


```
Warning: cannot open file 'testImpress.Rmd': No such file or directory
```

```
Error: cannot open the connection
```


<style>#impress-example pre{width: 95%}</style>






