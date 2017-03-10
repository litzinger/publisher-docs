---
title: Persistence
taxonomy:
    category: docs
---

Persistence is what Publisher uses to describe a 1 to 1 relationship for all content. All content is translated and the site is intended to operate as a "single tree" site. Meaning if a page or entry exists in one language, it exists in all languages. There are two settings which help enforce this, and they are Persistent Relationships and Persistent Grid.

The Grid field type allows for sub content within an entry and the Persistent Grid setting ensures that your translated entries have the same number of Grid rows as the default language. This is because under most circumstances content is entered in your default language, then translated to other languages, thus if you add 3 rows in your default language, it is assumed the same 3 rows will exist in all the translated content as well.

Grid and Relationship fields will visually behave differently when persistence is turned on. For example, + icons to add new rows will be removed from non-default languages. Relationship fields will be covered in a semi-transparent white screen to prevent mouse clicking to change the relationship in non-default languages. All this is to enforce persistence. If you do not like this behavior it can be disabled in the Publisher settings.

![A Grid field with Persistence enabled][http://docs.boldminded.com/images/disabled-grid.png]

Persistent Relationships work in the same way, meaning you can only alter the relationships when changing statuses. Changing the relationship field value when editing an entry in a different language will always use the relationships assigned to the default language version of the entry. There should be no reason to change a relationship from language to language, you are simply creating a link to another entry, which in itself should be translated.

![A Relationship field with Persistence enabled][http://docs.boldminded.com/images/disabled-relationship.png]

The same behavior applies to categories as well. A category is another form of a relationship. Under most circumstances all translations of an entry would have the same relationship or category assignments.

## Persistence explained

Lets say you have 3 languages, English (default), German, and French.

Persistence basically means that every piece of content exists in all languages. For example, if you have 10 entries in English, then it will assume there are translations for all 10 entries in all other languages and show those entries regardless if there is a translation for it (it will show the English content as a fallback).

When you turn persistence off and if you have the same 10 entries, but 2 of them do not have a German translation, then when you are viewing the site in German, the entries tag loop will only show 8 entries. The Persistent Grid and Relationship settings are similar, except it works with Grid rows instead of the entries.

The feature was added because many people had a site that 90% of the pages/content existed in all languages, however, they might have had a news/blog feed, for example, that the posts did not pertain to all languages (mostly due to localization, not strictly translation).

Generally people leave persistence turned on. If you are on a page of your site and expect a full translation of that page in any language, then persistence should benenabled. You can almost think of it as an MSM site, where each site may have different content (persistence turned off).

