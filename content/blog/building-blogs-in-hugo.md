+++
categories = ["web"]
color_choice = "#417505"
date = "2019-03-05T16:53:45+00:00"
draft = true
title = "Building Blogs in HUGO"

+++
Hugo is pretty cool, but I have been having some difficulties trying to convert a 'blog-less' theme into a theme that includes a blog.

I am still new to HUGO so what should be a simple task such as creating a list of blog posts and viewing said blog posts has had its hurdles. I have discovered a few 'oh duh' things about getting a blog to work, I am sure there will be more 'oh duh' moments in the future.

The first step in getting the blog listing to work was to make a `list.html` inside of a `layouts/defaults` folder... I did not realize for about an hour that I was missing this file, and the theme I was using didn't have a `layouts/_defaults` folder set up.

Great so now that I have my `list.html`  which was as simple as creating a file with the following ( I also forgot to add `{{.Content}}` for a while...)

    {{.Content}}
    {{ range .Pages }}
    <h2><a href="{{.URL}}">{{.Title}}</a>
    <small>{{.Date.Format "2006-01-02"}}</small>
    </h2>
    <p>{{.Description}}</p>
    {{ end }}

I should be able to see my blog posts by visiting `site.com/blog` yet there was nothing to be seen...

After some trouble shooting I realized my test blog post was still set to `draft: true` and so it didn't show up.

TL:DR; 

Make sure you set your posts to `draft: false` if you actually want them to be rendered by HUGO, and also make sure you have the very basic building blocks of `list.html` and `single.html` in your `layouts/_defaults` folder.

Once everything is configured properly it feels pretty good to be able to focus on writing.