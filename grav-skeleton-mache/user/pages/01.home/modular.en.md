---
title: Home
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
        custom:
            - _banner
            - _about
            - _services
            - _testimonials
            - _prices
            - _features
            - _cta1
            - _updates
            - _cta2
            - _cta3
            - _contact
            - _map
cache_enable: false
admin:
    children_display_order: collection
form:
    action: /home
    name: subscribe
    button_outer_classes: 'form-group col-md-6 col-sm-12'
    fields:
        -
            name: email
            label: Email
            placeholder: 'Your email address'
            type: email
            outerclasses: 'form-group col-md-12'
            classes: 'col-md-12 subscribe-mail'
            validate:
                required: true
        -
            name: g-recaptcha-response
            label: Captcha
            type: captcha
            outerclasses: 'form-group col-md-12'
            classes: col-md-12
            recaptcha_site_key: 6Lcl618UAAAAACsBh9ap_lP6_2-MMLAb-JkNaTFM
            recaptcha_not_validated: 'Captcha not valid!'
            validate:
                required: false
    buttons:
        -
            type: submit
            value: Subscribe
    process:
        -
            captcha:
                recaptcha_secret: 6Lcl618UAAAAAEFLlSCXb9bW5cdQmmQN-RMOuH05
        -
            email:
                subject: '[Site Contact Form] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: contact-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            display: thank-you
---

