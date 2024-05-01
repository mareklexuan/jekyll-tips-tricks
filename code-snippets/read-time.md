# Add "read time" to post

## Logic

- Count words in the document.
- Divide them reading rate (for example 265 word per minute)
- Display the result.

## Code snippet

```Liquid

    {% assign words = content | number_of_words %}
    {% if words < 265 %} 1 min read
    {% else %}
    {{ words | divided_by:265 | plus: 1 }} min read
    {% endif %}

```

## Notes

- For posts shorter than your reading rate, set fixed reading time as "1 minute".
- Liquid filter "divided_by:" rounds down to the nearest integer. To round up, just simply add +1 minute to read time.
