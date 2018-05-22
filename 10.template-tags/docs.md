---
title: Template Tags
taxonomy:
    category: docs
---

Publisher will create a ``{root_url}`` variable, which should be used in place of ``https://boldminded.com/`` if you are using the language segment prefix setting. The prefix adds an additional segment to your URL (but does not affect the ``{segment_N}`` variables), thus if you rely on https://boldminded.com/ to link things such as .css or .js files, they may not link properly. {root_url} will solve any linking problems you have because it is your main site URL without the language prefix.

It may also be more wise to use ``{page_url}`` in your templates instead of ``{page_uri}``, which does not get prefixed with a language segment. The only difference between the two variables is ``{page_url}`` contains the full URL including the language prefix. There is no real advantage to using ``{page_uri}``, even when not using Publisher.

Publisher comes with the following module tags and variables.

## ``{exp:publisher:switcher}``

This tag will add a dropdown menu to your site listing all the enabled languages and the URL needed to switch the site to the desired langauge. The dropdown menu will not work until you add your own JavaScript or form tag.

### Parameters

``style="links" (default: "select")``

Alternatively generate an unordered list of linked languages. Use this parameter to get up and running quickly. It will immediately let you change languages with no addtional JavaScript.

``show="1|4|9"``

Pipe delimited list of specific language IDs you wish to show. The language must still be enabled. If not defined all enabled languages will be displayed.

## ``{exp:publisher:languages}``

The languages tag will let you loop over all the enabled languages for whatever purpose you need. If you don’t like the ``{exp:publisher:switcher}`` tag, you can build your own switcher with this tag instead. It is best practice to use ``{switch_language_url}`` if you are using the languages tag as a language switcher.

```
{exp:publisher:languages}
    {short_name}
    {long_name}
    {id}
    {is_default}
    {is_enabled}
    {is_active}
    {direction}
    {switch_language_url}
    {translated_url}
{/exp:publisher:languages}
```

### Parameters

``show="1|4|9"``

Pipe delimited list of specific language IDs you wish to show. The language must still be enabled. Not necessary if you want to show all enabled languages.

``sort="2|3|1"``

Pipe delimited list to define the display order of the languages.

``show_current="no" (default: "yes")``

Defaults to yes. Set to "no" if you want to display all enabled languages except the currently active one.

``entry_id="123"``

If you pass an entry_id to this tag, it will see if a translation exists for the entry, and if no translation exists, it will skip to the next language. Most likely used in conjunction with the persistent entries setting when it is set to "no".

While the ``{canonical_url}`` variable is available, it is best to use ``{translated_url}`` to list out the translated versions of the current page. If URL Translations are off, this will still show the current URL, but with each language prefix. This approach is recommended by Google when creating multilingual sites when the URLs are different. For example, you can add this to your templates:

```
{exp:publisher:languages}
    <link rel="alternate" hreflang="{short_name}" href="{translated_url}">
{/exp:publisher:languages}
```

Which will yield the following HTML if you site has 3 languages:

```
<link rel="alternate" hreflang="en" href="http://www.example.com/en" />
<link rel="alternate" hreflang="fr" href="http://www.example.com/fr" />
<link rel="alternate" hreflang="de" href="http://www.example.com/de" />
```

## ``{exp:publisher:translate_entry}``

This is a simple module tag to fetch a translation of an entry in the current language being viewed. It does not parse 3rd part field type tags, e.g. Matrix or Playa. It is only meant as a simple query to the Publisher data. This is best used for modules that may not support Publisher yet, such as Calendar.

```
{exp:publisher:translate_entry entry_id="{entry_id}"}
    {title}
{/exp:publisher:translate_entry}
```

## ``{exp:publisher:translate_category}``

If you are not using the {exp:channel:categories} tag you might need to alter templates to translate categories. You can retrieve all translated information about a category with this tag.

### Parameters

``cat_id="{category_id}"``

Pass the ID of the category to retrieve.

``return="cat_name"``

Only required if using as a single tag, not a tag pair.

``lang_id="1|4|9"``

The language ID you would like to show a translation for. This is only required if you want to display the content in a language other than the current language.

```
{exp:publisher:translate_category cat_id="1"}
    {cat_name}
    {cat_url_title}
    {cat_description}
    {cat_image}
    {cat_order}
    {cat_id}
    {site_id}
    {group_id}
    {parent_id}
    {[custom_category_field]}
{/exp:publisher:translate_category}
```

This tag can alternatively be used as a single tag instead of a tag pair. In doing so you must specific which category field to return with the return parameter.

```
{exp:publisher:translate_category cat_id="1" return="cat_name"}
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

## Searching

Publisher works with the native ExpressionEngine search module, however, Publisher comes with a basic search tag.

```
{exp:publisher:search field_name="keyword|another keyword"}
    {exp:channel:entries entry_id="{entries}"}
        {title}
    {/exp:channel:entries}
{/exp:publisher:search}
```

### Parameters

``field_name="= keyword"``

Search for an exact word match

``field_name="not keyword|another string"``

Search for a "another string" but not "keyword"

``field_name="!= keyword|another string"``

Search for a "another string" but not "keyword"

``field_name="IS_EMPTY"``

Search to see if a particular field contains no value

## ``{exp:publisher:toolbar}``

This tag is will add a toolbar to your templates to allow specified users to toggle between the draft and published versions of a page and is only visible to members who have access to your control panel. No CSS or JavaScript is added to your page. It is up to you to style the toolbar. The markup is very specific and contains extra tags for your styling pleasure. You can also add text in the header and footer elements with CSS’s content property. Example tag output:

```
<div class="publisher-toolbar">
    <div class="publisher-toolbar-header"></div>
    <ul>
        <li class="publisher-toolbar-item">
            <a class="publisher-toolbar-link" href="..."><span>Draft<span></a>
        </li>
        <li class="publisher-toolbar-item">
            <a class="publisher-toolbar-link" href="..."><span>Published<span></a>
        </li>
    </ul>
    <div class="publisher-toolbar-footer"></div>
</div>
```

### Parameters

``status="draft|open"``

Only available if using the {exp:publisher:toolbar} tag as a single tag. Will return an anchor tag to be used to switch to the desired status. Usage example:

``{exp:publisher:toolbar status="open"}``

``{exp:publisher:toolbar status="draft"}``

Would return:

```
<a class="publisher-toolbar-link publisher-active-status" href="..."><span>Published<span></a>
<a class="publisher-toolbar-link" href="..."><span>Draft<span></a>
```

``active="publisher-active-status"``

Lets you change the active class name used on the link that is currently active. Defaults to publisher-active-status.

## Global Variables

``{publisher:current_language_id}``

An early parsed global variable that will give you the ID of the current language the site is being viewed in.

``{publisher:current_language_code}``

An early parsed global variable that will give you the language code (generally 2 characters) of the current language the site is being viewed in.

``{publisher:current_language_prefix}``

An early parsed global variable to reference the current language code, e.g. "en", "es", "de".

``{publisher:current_locale}``

An early parsed global variable that will give you the current locale as defined in the language, e.g. ``es_ES`` or ``fr-CA``.

``{publisher:default_language_id}``

An early parsed global variable that will give you the ID of the default language for the site.

``{publisher:default_language_code}``

An early parsed global variable that will give you the language code (generally 2 characters) of the default language for the site.

``{publisher:reserved_category_word}``

An early parsed global variable to give you the translated value of the reserved category word. Will use the default "category" value if not defined for a language.

``{publisher:entry_status}``

An early parsed global variable to use in your entries tags in order to view newly added drafts that have no corresponding open/published data. For example:

```
{exp:channel:entries status="your-custom-status{publisher:entry_status}"}
{/exp:channel:entries}
```

## Additional ``{exp:channel:entries}`` Parameters

Publisher makes a few extra variables available in your entries tags. If you need to know if an entry has a draft that is newer than the currently viewed published version, or if you need to know if the entry is fully translated to all available languages you can add the following parameter to your entries tag.

```
{exp:channel:entries publisher_fields="y"}
    {has_newer_draft}
    {is_translation_complete} // Is the entry translated to all languages?
    {has_translation} // Does the entry have a translation for any language other then the default?
    {is_translated} // Does this entry have a translation in the current language?
    {has_pending_approval} // Does this entry have a newer version pending approval?
    {publisher_lang_id}
    {publisher_status}
{/exp:channel:entries}
```

You can alternatively set the value of this parameter to something other than "y", it will then act as a variable prefix.

```
{exp:channel:entries publisher_fields="publisher:"}
    {publisher:has_newer_draft}
    {publisher:is_translation_complete}
    {publisher:has_translation}
    {publisher:is_translated}
    {publisher:has_pending_approval}
    {publisher:publisher_lang_id}
    {publisher:publisher_status}
{/exp:channel:entries}
```

To query entries by a specific status or language you can add the following parameters to your entries tag. When using the ``publisher_lang_id`` parameter it will query entries by the defined language, regardless of what the user currently has the site language set to.

```
{exp:channel:entries publisher_lang_id="2" publisher_status="draft|open"}
    ...
{/exp:channel:entries}
```

Even if you have Publisher’s cache option turned on in its settings, it does not mean entries tags are cached. The cache setting caches many behind the scenes queries for Publisher. To enable entry tag caching, you must enable Publisher’s cache, but also add the following parameter to your entries tags.

```
{exp:channel:entries publisher_cache="yes"}
    ...
{/exp:channel:entries}
```

## ``{exp:channel:prev/next_entry}``

Instead of using the native tags, you will need to use the Publisher specific versions of the tag. They are effectively the same thing noted in the ExpressionEngine documentation, just different names.

```
{exp:publisher:prev_entry}
    Prev entry: <a href="{path='site/comments'}">{title}</a>
{/exp:publisher:prev_entry}

{exp:publisher:next_entry}
    Next entry: <a href="{path='site/comments'}">{title}</a>
{/exp:publisher:next_entry}
```

## ``{exp:publisher:translate_url}``

This is a simple tag to translate a URL. Publisher will automatically translate URLs within links and form tags, however, there may be cases in which you would like to provide a translated URL outside of Publisher’s automatic processes.

```
{exp:publisher:translate_url url="path/to/some/page"}
```

## ```{exp:channel:form}``` tags

Publisher supports the Channel Form module, but you will need to add an additional parameter to the form tag. By adding ``publisher_status="open"`` to the tag it will load the open/published version of the entry for editing. Change it to ``publisher_status="draft"`` to edit the draft version. By default it will load the currently viewed language version of the entry. You can also use ``publisher_lang_id="1"`` to change the language of the entry. For example you can be viewing the site in English, but choose to edit the German version of the entry by changing the lang_id.

You will also need to add 3 hidden fields to your tag, which will determine which version of the entry should be displayed and how it will be saved. For example:

```
{exp:channel:form publisher_status="draft"}
    <input type="hidden" name="lang_id" value="{publisher:current_language_id}" />
    <input type="hidden" name="publisher_view_status" value="draft" />
    <input type="hidden" name="publisher_save_status" value="draft" />
{/exp:channel:form}
```

If you are building a multi-step form and only submitting a subset of fields on each step you may need to add an additional hidden field. Publisher will be able to tell which fields are submitted and which are not, however, the Title and URL Title fields are not able to be detected due to how EE handles the form submission data. For example, if you create a 2 step form, but don't want to display the Title and/or URL Title fields on step 2, you will need to add the following input. If you experience issues where fields that are not on a particular step of a form are still submitting, or saving blank values over existing values, then you may need to use the ```publisher_ignore_fields``` hidden input and separate the fields by the pipe character.

```
{exp:channel:form publisher_status="draft"}
    <input name="publisher_ignore_fields" value="title|url_title" type="hidden" />
{/exp:channel:form}
```

## Forms
Publisher will update all form tags (action and hidden form field parameters) with appropriately prefixed URLs. For example, ``action="path/to/page"`` will be updated with ``action="en/path/to/page"`` if English is your default value. If you wish to disable this functionality, add ``data-publisher-ignored="yes"`` to your form tags. This may be necessary for forms that post to external URLs, such as Campaign Monitor or another newsletter/subscription type service.

If you are using Freeform from Solspace, and using the language prefix option, you may need to update the return and any other URL based parameter in the Freeform tag to include the language prefix. Publisher is unable to automatically update this value due to how Freeform is processing the parameter values. For example, your return parameter may need to look like this:

```
{exp:freeform:form form_name="contact" return="{publisher:current_language_code}/template_group/template"}
```

## Email Notification Templates

ExpressionEngine's native **Message Pages > Email Notifications** templates can be updated to contain the two following variables:

### ``{translated_entry_url}``
This variable is exactly the same as the ``{entry_url}`` variable in the email templates in that it will create a URL based on the *Channel URL* in the Channel's Path Settings section suffixed with the entry's URL Title. The only difference is it will translate the URL accordingly.

### ``{preview_url}``
This variable will create a full URL to the entry based on its Page or Structure URL or the path defined in Publisher's Template Previews settings.
