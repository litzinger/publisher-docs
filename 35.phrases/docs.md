---
title: Phrases
taxonomy:
    category: docs
---

During installation Publisher will create two phrase groups. Default, and Languages. These two groups can not be deleted as Publisher expects them to be present. When a language is added it will also be added to the languages phrase group. The langauges phrase group is used by Publisher when listing site languages via the module tags so the language name itself can be translated to the end user.

Phrases are available in your template as early parsed global variables, e.g. ``{phrase:[phrase_short_name]}``

All phrases are also available in a single early parsed global variable called ``{current_phrases}`` (this variable name can be changed in the settings page). This variable will print a JSON object of all the phrases so you can reference them in your JavaScript files. For example:

```
<script type="text/javascript">
    var phrases = {current_phrases};
</script>
```

## ``{exp:publisher:translate_phrase}``

Although phrases are readily available via early parsed variables such as {phrase:some_word} you can also access them through a module tag. You may need to use this tag when you have a phrase name from another module variable or custom field value.

### Parameters

``name="some_word"``

Pass the phrase name without the prefix to return the translated value.

``replace="apples|oranges"``

If the replace parameter is provided, it will attempt to perform a vsprintf() function on the phrase contents. For example if your phrase is "The time is %s" and you add ``replace="{current_time}"`` to the tag, it will insert the current time into the phrase string. Using a pipe character in the replace parameter will indicate that it is an array of values, thus you should have multiple %s tokens in your phrase string.

``site_id="2"``

If you have a phrase with the same name in multiple sites you can choose which translation to return.

``escape="[html|attr]"``

When using the replace parameter there may be instances in which the phrase name contains a replace token (%s), and the contents contain html tags. Using the escape parameter will ensure the html tags are properly escaped.

```
{exp:publisher:translate_phrase_name="some_word"}
```

## ``{exp:publisher:phrases}``

A basic method to iterate over a group of phrases. In most cases you will use the early parsed global {phrase:X} variables, but in some cases you may need to list all phrases.

```
{exp:publisher:phrases group="default"}
     {phrase_id}
     {phrase_name}
     {phrase_value}
{/exp:publisher:phrases}
```
