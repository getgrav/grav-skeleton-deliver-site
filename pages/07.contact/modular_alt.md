---
title: 'Contact Us'
onpage_menu: '1'
body_classes: 'modular header-lite fullwidth'
bg_color: '#B4B093'
form:
    name: my-nice-form
    action: /contact
    fields:
        -
            name: name
            id: name
            label: Name
            classes: 'form-control form-control-lg'
            placeholder: 'Enter your name'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: email
            id: email
            classes: 'form-control form-control-lg'
            label: Email
            placeholder: 'Enter your email address'
            type: email
            validate:
                rule: email
                required: true
        -
            name: message
            label: Message
            classes: 'form-control form-control-lg'
            size: long
            placeholder: 'Enter your message'
            type: textarea
            validate:
                required: true
    buttons:
        -
            type: submit
            value: Submit
            classes: 'btn btn-primary btn-block'
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to:
                    - '{{ config.plugins.email.to }}'
                    - '{{ form.value.email }}'
                subject: '[Feedback] {{ form.value.name|e }}'
                body: "{% include 'forms/data.html.twig' %}"
        -
            save:
                fileprefix: feedback-
                dateformat: Ymd-His-u
                extension: txt
                body: "{% include 'forms/data.txt.twig' %}"
        -
            message: 'Thank you for your feedback!'
        -
            display: thankyou
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
sitemap:
    lastmod: '28-01-2025 16:24'
show_title: '1'
title_bg_choice: color
media_order: 'blog-header.png,pic06.jpg'
show_featured_image: true
featured_image: pic06.jpg
big_header: false
title_text_color: '#ffffff'
title_bg_color: '#b84e2b'
---

