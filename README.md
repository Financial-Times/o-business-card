# o-business-card [![Build Status](https://travis-ci.org/Financial-Times/o-business-card.svg?branch=master)](https://travis-ci.org/Financial-Times/o-business-card)

Render contact information about a FT employee (Eg, name, email, twitter handle...).

To render a business card, you just need to pass a JSON to the template with that person's details. Here's a list of all possible values (it can be extended):

- name
- image
- url
- bio
- email
- twitter
- age
- nationality
- background

At least values for "name", "image" and "url" need to be passed, and the last two should be absolute URLs. The other values are optional.

The image can either be floated left or right depending on the modifier of the class selector: "--left" or "--right".

## Structured data

Every business card will be using structured data using schema.org, a collaboration by Google, Microsoft and Yahoo. This will help search engines understand each person's details better. We're using microdata to structure the data. 

Each o-business-card component will be an itemscope that gets its itemtype from [http://schema.org/Person](http://schema.org/Person). And then each element has its corresponding itemprop, except for "age":

- name
- image
- url
- description
- email
- sameAs (it tells search engines that this URL also references this person)
- nationality

## Silent Mode

By default the SASS is in silent mode, meaning there will be no CSS output.

If you're `@import`ing the SASS into your product or component, and you want to turn off silent mode, then set the following SASS variable:

```sass
$o-business-card-is-silent: false;
```

If requesting the CSS from the build service, silent mode will automatically be switched off.

In silent mode, instead of the CSS classes listed below, there will be SASS mixins using a camel-cased version of the class name, ie `@include oBusinessCard` instead of a `.o-business-card` selector.

## Markup

Please see [main.mustache](https://github.com/Financial-Times/o-business-card/blob/master/main.mustache).
