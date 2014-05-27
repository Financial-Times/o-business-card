# o-business-card [![Build Status](https://travis-ci.org/Financial-Times/o-business-card.svg?branch=master)](https://travis-ci.org/Financial-Times/o-business-card)

Render contact information about a FT employee (Eg, name, email, twitter handle...).

To render a business card, you just need to pass a JSON to the template with that person's details. Here's a list of possible values:

- name
- image
- url
- bio
- email
- twitter
- age
- nationality
- background

At least values for "name", "image" and "url" need to be passed, and the last two should be absolute URLs. The other values are optional and those elements will only be displayed if the templated receives those values.

The image can either be floated left or right depending on the modifier of class selector: "--left" or "--right". 

## Markup

```html
<div data-o-component="o-business-card" data-o-version="0.1.0" class="o-business-card">
    <img src="{{image}}" class="o-business-card__image--right" />
    <p>
        <a href="{{url}}" class="o-business-card__name">{{name}}</a>
        {{#bio}}<span class="o-business-card__bio">{{bio}}</span>{{/bio}}
    </p>
    {{#email}}<p><a href="mailto:{{email}}" class="o-business-card__email">{{email}}</a></p>{{/email}}
    {{#twitter}}<p><a href="https://twitter.com/{{twitter}}" class="o-business-card__twitter">@{{twitter}}</a></p>{{/twitter}}
    {{#age}}<p class="o-business-card__age"><span class="o-business-card__subtitle">Age: </span>{{age}}</p>{{/age}}
    {{#nationality}}<p class="o-business-card__nationality"><span class="o-business-card__subtitle">Nationality: </span>{{nationality}}</p>{{/nationality}}
    {{#background}}<p class="o-business-card__background"><span class="o-business-card__subtitle">Background: </span>{{background}}</p>{{/background}}
</div>
```

TO DO

- Use some form of [structured data](https://support.google.com/webmasters/answer/146646) - RDFa?