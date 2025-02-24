---
title: Kontakt
sitemap:
  changefreq: yearly
  priority: 0.7
  lastmod: 11-02-2024
date: 11-02-2024

form:
  name: contact-form
  fields:
    names:
      type: columns
      fields:

        col1:
          type: column
          fields:
            firstname:
              type: text
              label: Vorname
              placeholder: Max

        col2:
          type: column
          fields:
            lastname:
              type: text
              label: Nachname
              placeholder: Mustermann

    email:
      type: email
      label: 'E-Mail Adresse'
      placeholder: max.mustermann@example.com
      validate:
        required: '1'

    subject:
      type: text
      label: Betreff
      placeholder: 'Ihr Anliegen'
      validate:
        required: '1'

    message:
      type: textarea
      label: Nachricht
      placeholder: 'Ihre Nachricht an uns.'
      validate:
        required: '1'

    turnstile:
      type: turnstile
      theme: light

  buttons:
    submit:
      type: submit
      value: Senden
      classes: 'btn btn-primary'
    reset:
      type: reset
      value: Zurücksetzen

  process:
    turnstile: true
    email:
      from: '{{ config.plugins.email.from }}'
      to:
        - '{{ config.plugins.email.to }}'
      subject: '[Kontaktformular]: {{ form.value.subject|e }}'
      body: '{% include ''forms/data.html.twig'' %}'
    display: thankyou
    message: 'Wir haben Ihre Nachricht erhalten und werden uns in Kürze bei Ihnen melden.'
---

# Kontakt

Kontaktieren Sie uns bitte über folgende E-Mail Adresse: [kontakt@crabston.ch](mailto:kontakt@crabston.ch). Alternativ können Sie auch über das Kontaktformular mit uns Kontakt aufnehmen.
