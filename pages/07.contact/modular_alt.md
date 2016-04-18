---
title: Contact Us
onpage_menu: false
body_classes: "modular header-lite fullwidth"
bg_color: "#B4B093"
form:
    name: my-nice-form
    action: /contact
    fields:
        - name: name
          id: name
          label: Name
          classes: form-control form-control-lg
          placeholder: Enter your name
          autocomplete: on
          type: text
          validate:
            required: true

        - name: email
          id: email
          classes: form-control form-control-lg
          label: Email
          placeholder: Enter your email address
          type: email
          validate:
            rule: email
            required: true

        - name: message
          label: Message
          classes: form-control form-control-lg
          size: long
          placeholder: Enter your message
          type: textarea
          validate:
            required: true

    buttons:
        - type: submit
          value: Submit
          class: btn btn-primary btn-block

    process:
        - email:
            from: "{{ config.plugins.email.from }}"
            to:
              - "{{ config.plugins.email.from }}"
              - "{{ form.value.email }}"
            subject: "[Feedback] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: feedback-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - message: Thank you for your feedback!
        - display: thankyou    
content:
    items: @self.modular
    order:
        by: default
        dir: asc
---
