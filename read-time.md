# Add "read time" to post

## Logic

1. Count words in the document
2. Divide them reading rate (for example 265 word per minute)
3. Display result

```Liquid

    {% assign words = content | number_of_words %}
    {% if words < 265 %} 1 min read
    {% else %}
    {{ words | divided_by:265 | plus: 1 }} min read
    {% endif %}

```

## Notes

- For posts shorter than your reading rate, set fixed reading time as "1 minute".
- Liquid filter "divided_by:" rounds down to nearest integer. To round up, just simply add +1 minute to read time.
