---
title    : Layouts
subtitle : Slidify Workshop
author   : Ramnath Vaidyanathan
mode     : selfcontained # {standalone, draft}
url      : {lib: "../../libraries"}
hitheme  : solarized_light
widgets  : [bootstrap]
editlink : "tutorials/02"
assets:
  js:
    - "http://ajax.googleapis.com/ajax/libs/jqueryui/1.10.3/jquery-ui.min.js"
    - "http://bartaz.github.io/sandbox.js/jquery.highlight.js"
--- .segue .dark .nobackground

<q>A layout is a mustache template that specifies the markup to render a slide</q>

*** =pnotes

Layouts allow a clean separation of content from design, thereby allowing the same markdown document to be rendered using multiple HTML5 frameworks. The best way to understand layouts is to follow a slide through slidify

--- .segue .dark

## Journey of a Slide

---

<iframe src='../01/assets/img/raw_slide.svg' width=800px height=250px>
</iframe> 

--- .centrepre .bigger

## Slide

    --- {class: class1, bg: yellow, id: id1}
    
    ## Slide Title
    
    Slide Contents


--- .centrepre .bigger &callout #slide1a

## Slide




    --- {class: class1, bg: yellow, id: id1}
    
    ## Slide Title
    
    Slide Contents

*** .left

Properties

--- .centrepre .bigger &callout #slide1b

## Slide

    --- {class: class1, bg: yellow, id: id1}
    
    ## Slide Title
    
    Slide Contents

*** .left

Title

--- .centrepre .bigger &callout #slide1c

## Slide

    --- {class: class1, bg: yellow, id: id1}
    
    ## Slide Title
    
    Slide Contents
    
*** .left

Content

---

<iframe src='../01/assets/img/parse_slide.svg' width=800px height=250px>
</iframe> 

--- #payload .centrepre

## Payload


```
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

$id
[1] "id1"
```


---

<iframe src='../01/assets/img/layout_slide.svg' width=800px height=250px>
</iframe> 



--- .RAW .bigger .centrepre #layout

## Layout

```html
<slide class="{{ slide.class }}" id="{{ slide.id }}" 
    style="background:{{{ slide.bg }}};">
  <hgroup>
    {{{ slide.header}}}
  </hgroup>
  <article>
    {{{ slide.content }}}
  </article>
</slide>
```

---

<iframe src='../01/assets/img/render_slide.svg' width=800px height=250px>
</iframe>

--- .bigger .centrepre #rendered

## Rendered


```
<slide class="class1" id="id1" style="background:yellow;">
  <hgroup>
    <h2>Slide Title</h2>
  </hgroup>
  <article>
    <p>Slide Contents</p>

  </article>
</slide>
```


--- {class: class1, bg: yellow, id: id1}
    
## Slide Title
    
Slide Contents

--- .segue .dark .nobackground

## Inheritance

--- .centrepre .RAW &vcenter .bigger

## Adding a Footer

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

## Adding a Footer

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

## Adding a Footer

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

## Custom Layouts

--- .centrepre #carouselslide .carouselslide

## Carousel



	--- {tpl: carousel, class: span12}
	    
	## Carousel
	    
	    
	*** {class: active, img: "../01/assets/img/split.svg"}
	    
	Image 1
	    
	*** {img: "../01/assets/img/apply.svg"}
	    
	Image 2


--- .centrepre #carouselslideA &callout .carouselslide

## Carousel

```no-highlight

 --- {tpl: carousel, class: span12}
     
 ## Carousel
     
     
 *** {class: active, img: "../01/assets/img/split.svg"}
     
 Image 1
     
 *** {img: "../01/assets/img/apply.svg"}
     
 Image 2

```

*** .left

Properties


--- .centrepre #carouselslideB &callout .carouselslide

## Carousel

```no-highlight

 --- {tpl: carousel, class: span12}
     
 ## Carousel
     
     
 *** {class: active, img: "../01/assets/img/split.svg"}
     
 Image 1
     
 *** {img: "../01/assets/img/apply.svg"}
     
 Image 2

```

*** .left

Title

--- .centrepre #carouselslideC &callout .carouselslide

## Carousel

```no-highlight

 --- {tpl: carousel, class: span12}
     
 ## Carousel
     
     
 *** {class: active, img: "../01/assets/img/split.svg"}
     
 Image 1
     
 *** {img: "../01/assets/img/apply.svg"}
     
 Image 2

```

*** .left

Blocks

--- .RAW .smaller

<a class='example'>layout</a>

	 ---
	 layout: slide
	 ---
	 
	 {{{ slide.content }}}
	 <div id="{{slide.id}}-carousel" class="carousel slide {{slide.class}}">
	   <!-- Indicators -->
	   <ol class="carousel-indicators">
	     {{# slide.blocks }}
	     <li data-target="#{{slide.id}}-carousel" data-slide-to="{{num}}" class="{{class}}"></li>
	     {{/ slide.blocks }}
	   </ol>
	   <!-- Wrapper for slides -->
	   <div class="carousel-inner">
	     {{# slide.blocks }}
	     <div class="item {{class}}">
	       <img src="{{img}}" alt="{{alt}}">
	       <div class="carousel-caption">{{{ content }}}</div>
	     </div>
	     {{/ slide.blocks }}
	   </div>
	   <!-- Controls -->
	   <a class="left carousel-control" href="#{{slide.id}}-carousel" data-slide="prev">&lsaquo;</a>
	   <a class="right carousel-control" href="#{{slide.id}}-carousel" data-slide="next">&rsaquo;</a>
	 </div>


--- &carousel .span12 #mycarouselslide

<a class='example'>view</a>


*** {class: active, img: "../01/assets/img/split.svg"}

Image 1

*** {img: "../01/assets/img/apply.svg"}

Image 2

<style>
#mycarouselslide img {
  width: 800px;
  height: 600px;
}
</style>

--- .dark .segue .nobackground

## Notes

---

## Properties

Slide properties are key-value pairs that are passed to the layout. You can specify class, id and bg and style the slide, either by using built in classes, or specifying additional css.

    --- {class: [class1, class2], id: id}

You can also use symbolic css style prefixes for frequently used properties. For instance, a dot indicates class, a hash refers to id and an ampersand identifies a layout.

    --- .class1 .class2 #id


---
    
## Properties

| **Variable**    | **Description**                       |
|-----------------|---------------------------------------|
| `slide.title`   | The title of the slide with no markup |
| `slide.header`  | The title of the slide with markup    |
| `slide.level`   | The title header level (h1 - h6)      |
| `slide.content` | The contents of the slide sans header |
| `slide.html`    | The contents of the slide with header |
| `slide.num`     | The number of the slide               |
| `slide.id`      | The id assigned to the slide          |
| `slide.class`   | The class assigned to the slide       |
| `slide.bg`      | The background assigned to the slide  |
| `slide.myblock`   | The slide block named myblock       |
| `slide.blocks`  | The slide blocks which are not named  |
| `slide.rendered`| The rendered slide                    |

---

## Blocks

Blocks are slides nested within a slide, identified by three stars. Just like a slide, they can contain  properties, title and content. 

There are two types of blocks - named and unnamed. A block can be named by specifying the property `{name: block1}` (or using the symbolic shortcut `{=block1}`). 

A block with the name `block1` can be accessed in a slide layout as `slide.block1`. The title and content of this block can be accessed as `slide.block1.title` and `slide.block1.content`. Unnamed blocks are aggregated into the namespace `slide.blocks`. 










