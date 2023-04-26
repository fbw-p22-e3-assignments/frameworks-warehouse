# Consume REST APIs using Python

## Topics covered

Using REST APIs with Python and Django to obtain data.

## Goal achieved

You will add a banner in your site with up to date information on the COVID-19 cases in the country of origin of your website's visitor.

## Description

With the queries and knowledge you have from [the previous individual project milestone](../2_Consume_REST_Postman/), get the country of origin of your visitor (use the `request.META` dictionary) and show a banner in your website with the following:

- The flag of the country and its common name in the native language.
- The total population of the country.
- The ratio of COVID-19 confirmed, recovered, critical and death cases for 100.000 inhabitants.
- The total amount of confirmed, recovered, critical and deaths.
- The date of the last update of the COVID-19 data.

> HINT: When working on development you may only be getting the private IP (127.0.0.1). Define a `get_client_ip` function that returns a hard-coded IP if Django's `settings.DEBUG` is set to True.
