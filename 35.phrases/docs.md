<img src="https://boldminded.com/assets/publisher/phrases.png" />

During installation Publisher will create two phrase groups. Default, and Languages. These two groups can not be deleted as Publisher expects them to be present. When a language is added it will also be added to the languages phrase group. The langauges phrase group is used by Publisher when listing site languages via the module tags so the language name itself can be translated to the end user.

Phrases are available in your template as early parsed global variables, e.g. ``{phrase:[phrase_short_name]}``

All phrases are also available in a single early parsed global variable called ``{current_phrases}`` (this variable name can be changed in the settings page). This variable will print a JSON object of all the phrases so you can reference them in your JavaScript files. For example:

```
<script type="text/javascript">
    var phrases = {current_phrases};
</script>
```