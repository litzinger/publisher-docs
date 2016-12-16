---
title: Url Translations
taxonomy:
    category: docs
---

Publisher supports URL translations through the native ``template_group/template``. To translate template names, go to ``Add-ons > Modules > Publisher > Templates``. There you can define the names of your templates for each language. You will also have to make a slight adjustment to your ``{exp:channel:entries}`` tag. The main entries tag used to render the page will need to have ``dynamic_parameters="entry_id"`` parameter added to it:

```
{exp:channel:entries dynamic_parameters="entry_id"}
    // code here
{/exp:channel:entries}
```

Due to the ability to have multiple entries tags in a template, this is the only reliable way Publisher can determine the translated ``url_title`` value for the page.

Publisher also creates its own segment variables. It is common to use the ``url_title`` parameter on an entries tag, or 3rd party module tags to query an entry. When using translated URLs your ``{segment_N}`` variables will contain the translated value, which won't find the entries you are searching for. ExpressionEngine's internals will expect a ``url_title`` in the default language. To reliably use the ``url_title`` parameter in an entries tag Publisher creates additional segment variables you can use. These variables are in the following format: ``{publisher:segment_N}`` and ``{publisher:last_segment}`` A usage example is:

```
{exp:channel:entries url_title="{publisher:segment_3}"}
    // code here
{/exp:channel:entries}
```

While you can have translated or draft versions of your URLs, *all* languages and states (draft or published) will share the same structure tree, which is to say, you can not create a draft entry with a page at a different level of the navigation tree than the published version. Publisher is designed to follow the single tree model, in that everything is 1 to 1 relationship. For every default language version of an entry there should be a translated version at the same location, thus the navigation tree would be the same.

>>> URL Translations is an intensive process which requires template files to be re-parsed to update path variables with the translated version. Caching is recommended if you plan to use this feature.

## Canonical URL
If URL Translations are enabled you will have access to an early parsed global variable called ``{canonical_url}`` which will always be set to the default language value of the current URL being viewed. It also does not contain any query parameters or hashes if they exist in the translated version.

## Path Variables
The following variables are supported in URL translation: ``{url_title_path=""}``, ``{entry_id_path=""}`` and ``{path=""}``