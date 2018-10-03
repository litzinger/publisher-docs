---
title: Categories
taxonomy:
    category: docs
---

Categories in Publisher are managed differently than phrases, even if the management forms appear similar. You can not
create a new category group or category in Publisher itself. The "New" and "Edit" actions will take you out of Publisher's
settings pages and into native ExpressionEngine category management. Publisher only manages the translations of a category
after it has been created. Publisher also does not translate the category group names.

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
