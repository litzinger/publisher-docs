---
title: Language Settings
taxonomy:
    category: docs
---

## Long Name
Long Name is the full text name of the language, e.g. English, Italian, French etc. This is the value used in the language drop down menu in the toolbar, and the default translation of the language in the module tags.

## Short Name
Short Name is the language code. Language codes are generally 2 characters and generally follow the ISO 639-1 standard. It is important to follow this standard if you wish to let Publisher determine the user’s langauge based on their browser language. The short name is also used in your URL if you have the URL Prefix option set to yes. The first segment of your URL will be replaced by this value.

## Locale
Publisher lets you define a locale, which should be in the following format ``en_EN`` or ``fr_CA``, however, it is not used for any language identification or switching logic. It is only provided as a property for each language that could be used for template purposes such as setting meta tags, e.g. ``<meta property="og:locale" content="en_US">`` and ``<meta property="og:locale:alternate" content="de_DE">``

## Is Default
Only one language can be set as your default. This is the language in which all your content will be entered in first before translations are entered. It is also the language that will be displayed on the site if the “Get language from browser” setting is set to No and it is the user’s first time visit to the site and has not choosen a language.

## Is Enabled
Languages can be disabled. Disabling a language means that it is only removed from the {exp:publisher:switcher} and {exp:publisher:languages} module tags, effectively removing it as an option that users can select. If disabled the language will still be availalbe within the control panel for editing, and accessible on the front-end of the site if the user manually changes the URL string. For example, if Spanish is disabled, but the user changes the URL from site.com/en/page to site.com/es/page the Spanish page will still load if it exists.

## Text Direction
Each language has the option of setting a text direction. If set to **Right to Left**, all custom fields on the publish page will display the text right to left if able. This will apply to all text, textarea, and WYSIWYG based editors. Publisher will also create a global variable to use in your templates called ``{text_direction}``. You can use this in your HTML markup to set dir attribute on your elements. For example: ``dir="{text_direction}"``.

## Language Pack
Assign a core ExpressionEngine language pack to the language so system messages will appear translated to the user. You can download language packs from EllisLab.