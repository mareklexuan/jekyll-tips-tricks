# Add "read time" to post

```Liquid

    {% assign words = content | number_of_words %}
    {% if words < 265 %} 1 min read
    {% else %}
    {{ words | divided_by:265 | plus: 1 }} min read
    {% endif %}

```
