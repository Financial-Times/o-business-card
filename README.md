o-business-card
===============

Render contact information about a FT employee (Eg, name, email, twitter handle...).

MUST

- Represent the main attributes of a FT journalist - name/byline, email, photo
- Use some form of [structured data](https://support.google.com/webmasters/answer/146646) - RDFa?

```html
<div
    data-o-component="o-business-card"
    data-o-version="0.1.0"
    class="o-business-card"
    vocab="http://schema.org/"
    typeof="Person"
    >
    <span property="name" class="o-business-card__name">
        <a href="{{http://www.ft.com/path/to/profile}}" property="url" class="o-business-card__url">
            {{Richard Stovin-Bradford}}
        </a>
    </span>
    <img src="{{path/to/head-shot}}" property="image" class="o-business-card__image" />
    <a href="mailto:{{richard.stovin-bradford@ft.com}}" property="email" class="o-business-card__email">
        {{richard.stovin-bradford@ft.com}}
    </a>
    <a href="https://twitter.com/StovinBradford" class="o-business-card__twitter">
        @StovinBradford
    </a>
</div>
```

TBD

- You could argue this is essentially to a byline, so should be named that.


