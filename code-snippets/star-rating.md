# Star rating

Code snipped how to add star rating (1-5 stars).

## Logic

- On every post, have the Front Matter variable `rating` as an integer of defined star rating range (I am using 1-5).
- You have two icons for each star rating - "full" rating (usually gold star) and "empty" rating (greyed out).
- Using Liquid, loop through range of numbers - you use it as counter - and for each number, display corresponding icon:
  - **Full rating** - Loop through a range of numbers from 1 to `rating` value. For example, 1 to 3.
  - **Empty rating** - Loop through the range of numbers from 1 to max rating minus `rating`. In our example, 1 to 2.

## Code snippet

Front Matter

```Front Matter
---
rating: 3
---
```

In your template:

```HTML

{% for i in (1..{{page.rating}}) %}
<img class="star-rating" src="{% link assets/icons/star-rating-full.svg %}" />
{% endfor %}

{% assign neg = 5 | minus: {{page.rating}} %}
{% for i in (1..neg) %}
<img class="star-rating" src="{% link assets/icons/star-rating-empty.svg %}" />
{% endfor %}
```

## Notes

- For "empty" rating, you need to calculate the remaining stars. It is not possible to do it directly in the loop range, so I am using the variable `neg` to first calculate the remaining stars and then use it as the limit of the range.
- HTML tag `<img>` is inline, so the icons will be rendered next to each other.
- I am using two preformatted icons, for full star and empty star, formatted directly in SVG. Using two different icons makes it easier to demonstrate and understand the Liquid templates to distinguish between `full star` and `empty stars`. rating. However, using two preformatted icons is not a scalable solution, as you have an extra file and you don't have a default global style of icon. Better solution is to use one icon, create two CSS classes and style icons separately with CSS.
