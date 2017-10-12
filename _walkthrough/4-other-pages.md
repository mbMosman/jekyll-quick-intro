---
title: Other Pages & Resources
previous_page: 3-blog-posts
next_page: 5-theme-layout
---

## Organization
A Jekyll site has two types of content:

- renderable content such as posts which have YAML front matter
- static content (images, PDFs, etc) that does not.

By default, any file or folder that is in the project folder and starts with an underscore (\_) is not moved into the build directory. The other files are processed (if they have front matter) and rendered to the build directory (`_site` by default).  Files in directories beginning with an underscore are handled as specified through the configuration.  

Themes will typically set up a folder called `assets` which is used to contain static files used by the theme. It is possible to store your own content there, but it often makes more sense to keep a clean separation between your content and the theme. If you decide to change you theme, you'll appreciate knowing clearly what can go and what must stay. If you look at the source for this site, you'll notice that an `images` folder was added to the root of the project to contain the image files used in my content.

Renderable content is often, but not always, found in the directories that begin with an underscore. Any content that is included and has YAML is renderable. We've already explored the Posts found in the `_posts` directory.  And we've seen the Home page, the index.md file that is found in the root project directory.

Other content pages, such as the About (about.md) can be added similarly by adding the appropriate front matter. They can either be placed in either the root project folder or they can be organized in static folders (ones that do not start with an underscore).  You are free to organize these files as you please, but keep in mind their final web URL may not match their location in the project file structure.

Take a look at the About page using the link on the top right of the Home page.  Notice that the file path is not `/my-first-site/about.html` as you might expect.

{% include image.html path="/about-page-url.png" alt="Image of About page showing URL." %}

As the site builds and your pages are rendered, they are often moved. The About page has a `permalink` property setup in the page front matter:

```
---
layout: page
title: About
permalink: /about/
---
```

This is what causes the file to be rendered at `/about/index.html`. You can find it there in the `_site` folder.  This permalink allows you to have neat, tidy URL's for your pages. However, it also provides a fixed URL, allowing you to reorganize your site and files without breaking links.

## Collections
Jekyll also allows you to organize and group files into Collections.  These are configured in the `_config.yml` file.  A `walkthrough` collection was created for the main pages of this site.  This provides a set of files that we can easily process dynamically using [Liquid Tags]().

To setup the Collection, first define it in `_config.yml`:

{% highlight YAML %}
collections:
  walkthrough:
    output: true
    permalink: /:collection/:name/
{% endhighlight %}

The Collection is expected to be in the `_walkthrough` directory.  The `output` property indicates that the files should be rendered to HTML, and the permalink uses the collection name and the file name to build the path.

Jekyll also allows you to setup default properties for the content. This is also added to  `_config.yml`.  The configuration below sets up a default layout of "walkthrough" for all files in the walkthrough Collection.

{% highlight YAML %}
defaults:
  -
    scope:
      path: ""
      type: walkthrough
    values:
      layout: walkthrough
{% endhighlight %}

On the index.md page, I use a loop to add links to all of the pages in the collection:

{% include image.html path="/collection-template.png" alt="Template for collection display." %}


## Data Files
Jekyll also allows you to add data files to your site.  It supports loading data from YAML, JSON, and CSV.  These files must be placed in the `_data` directory. This allows you to adda variety of data content to your site without overloading your `_config.yml` with content oriented information that isn't related to your theme or site build.   

Data files are pretty straightforward, and you can read more about them in the [Jekyll Docs](http://jekyllrb.com/docs/datafiles/).


Next let's look at how we can customize our site layout and theme.
