---
title: Themes & Custom Layout
previous_page: 4-other-pages
next_page: 6-learn-more
---

## View the theme
Before we start changing the theme and layout, it's helpful to see what we already have. The minima themes is installed as a Ruby gem.  To view it, do one of the following:

__On MacOS__
`open $(bundle show minima)`

__On Windows__
`explorer /usr/local/lib/ruby/gems/2.3.0/gems/minima-2.1.0`

You'll notice that the theme is setup with the following directories:

- `_includes`
- `_layouts`
- `_sass`
- `assets`

We've already talked about assets, and the SASS directory is pretty self explanatory. So what about the includes and layout?

## Includes
Includes are snippets of HTML that you can configure and pass input values to.  This site overrides the `footer.html` and `head.html` from the theme to slightly alter their display. It also adds an image.html, which I have gotten in the habit of creating to ensure that my images are styled consistently.

The `image.html` include contains the following:
{% highlight html %}
<div class="img-container">
  <img src="{{ site.baseurl }}/images/{{ include.path }}" alt="{{ include.text }}">
</div>
{% endhighlight %}

It is used in pages by adding an include tag:
```
{% include image.html path="/about-page-url.png" text="Image of About page showing URL." %}
```  

The `path` and `text` are input variables on the include and are referenced as `include.path` and `include.text` (inside the double curly brackets).

## Layout
Layouts are the templates for your site content.  They are chosen based on the layout property configured in the YAML front matter or `_config.yml` file.  The default layouts are found in the theme, but you can override those by adding a `_layouts` folder to your site with a layout of the same name.

The "minima" home layout looks like this:
{% include image.html path="/home-layout.png" alt="Template for home layout." %}

However for this site I have overridden that layout to just show the content from the
{% include image.html path="/home-layout-override.png" alt="Template for home layout." %}
