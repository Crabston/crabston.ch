---
title: Kontakt
sitemap:
  changefreq: yearly
  priority: 0.7
  lastmod: 17-02-2026
date: 17-02-2026

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

    phone:
      type: tel
      label: 'Telefonnummer'
      placeholder: +41 12 345 67 89
      validate:
        required: '0'

    sub:
      type: columns
      fields:

        col1:
          type: column
          classes: 'width-auto'
          fields:
            service:
              type: select
              label: Dienstleistung
              placeholder: 'Wählen Sie eine Dienstleistung aus'
              data-default@: ['\Grav\Theme\Hadron::getUriQueryParam', 'service']
              options:
                website: 'Website'
                webshop: 'Webshop'
                support: 'IT Support'
              validate:
                required: '1'

        col2:
          type: column
          fields:
            subject:
              type: text
              size: long
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

<style>
.width-auto {
	width: auto !important;
}
</style>

# Kontakt

Kontaktieren Sie uns gerne über das folgende Formular oder per E-Mail an [safe-email autolink="true" icon="envelope-o"]kontakt@crabston.ch[/safe-email]. Wir werden uns so schnell wie möglich bei Ihnen melden.
