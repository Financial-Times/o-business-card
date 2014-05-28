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

At least values for "name", "image" and "url" need to be passed, and the last two should be absolute URLs. The other values are optional and those elements will only be displayed if the template receives those values.

The image can either be floated left or right depending on the modifier of the class selector: "--left" or "--right".

## Structured data

Every business card will be using structured data using schema.org, a collaboration by Google, Microsoft and Yahoo. This will help search engines understand each person's details better. We're using microdata to structure the data. 

Each o-business-card component will be an itemscope that gets it's itemtype from [http://schema.org/Person](http://schema.org/Person). And then each element has it's corresponding itemprop, except for "age":

- name
- image
- url
- description
- email
- sameAs (it tells search engines that this URL also references this person)
- nationality

## Markup

```html
<div data-o-component="o-business-card" data-o-version="0.2.0" class="o-business-card" itemscope itemtype="http://schema.org/Person">
    <img src="{{image}}" class="o-business-card__image--right" itemprop="image" />
    <p>
        <a href="{{url}}" class="o-business-card__name" itemprop="url"><span itemprop="name">{{name}}</span></a>
        {{#bio}}
        <span class="o-business-card__bio" itemprop="description">{{bio}}</span>
        {{/bio}}
    </p>
    {{#email}}
    <p>
        <a href="mailto:{{email}}" class="o-business-card__email" itemprop="email">{{email}}</a>
    </p>
    {{/email}}
    {{#twitter}}
    <p>
        <a href="https://twitter.com/{{twitter}}" class="o-business-card__twitter" itemprop="sameAs">@{{twitter}}</a>
    </p>
    {{/twitter}}
    {{#age}}
    <p class="o-business-card__age">
        <span class="o-business-card__subtitle">Age: </span>{{age}}
    </p>
    {{/age}}
    {{#nationality}}
    <p class="o-business-card__nationality">
        <span class="o-business-card__subtitle">Nationality: </span>
        <span itemprop="nationality"> {{nationality}}</span>
    </p>
    {{/nationality}}
    {{#background}}
    <p class="o-business-card__background">
        <span class="o-business-card__subtitle">Background: </span>
        <span itemprop="description">{{background}}</span>
    </p>
    {{/background}}
</div>
```