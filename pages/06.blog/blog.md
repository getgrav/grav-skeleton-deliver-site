---
title: Blog
blog_url: blog
menu: Blog
body_classes: header-lite fullwidth blogstyling
bg_color: "#B4B093"

sitemap:
    changefreq: monthly
    priority: 1.03

content:
    items: @self.children
    order:
        by: date
        dir: desc
    limit: 5
    pagination: true

feed:
    description: Sample Blog Description
    limit: 10

pagination: true
---

# Our Blog
