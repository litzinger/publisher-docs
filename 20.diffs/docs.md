---
title: Diffs
taxonomy:
    category: docs
---

Publisher provides content diffs to show which content has been changed in your drafts. This feature is available in several configurations and options. A diff is a comparison of the open/published version of your content to the draft version. The draft is considered the newest revision, thus diffs are only available when viewing an draft, either in the control panel or the front-end of your site.

Content diffs are not available for phrases or categories.

<a href="http://boldminded.com/assets/images/uploads/publisher-diff-example.png" class="fancybox"><img src="http://boldminded.com/assets/images/uploads/publisher-diff-example-sm.png" class="float_right" /></a>

>>> Diffs will not work on the front-end of your site for content inside of {layout:set} variables.

Once installed you will need to enable Diffs in the Publisher settings page, and select which driver to use. Diffs can be enabled or disabled on your entry publish page and the front-end of your site, and you can optionally provide a text only diff.

>>> Running a diff on HTML content is very complicated unless done on a line by line basis. Opening and closing HTML tags are difficult to track, especially when text around them has changed. For this reason <i>do not</i> expect a perfect diff of your content. Added and removed text will be displayed, but an opening or closing HTML tag may appear in an incorrect location, thus causing the display of the diff to appear slightly different than your actual content.

## Global Diff Settings

The following global settings are available to configure Diffs in the Publisher Settings page.

### Diff Driver
As mentioned above, select which driver/library to use to parse the diffs.

### Diff Enabled (front-end)
Show content diffs on the front-end of your site when viewing a draft? Requires ``?publisher_status=draft`` in the URL. Use the <a href="https://boldminded.com/add-ons/publisher/template-tags">Publisher Toolbar</a> to toggle between Published and Draft content.

### Diff Enabled (CP)
Show content diffs next to each field on the publish page in the CP.

### Diff Style
A Full diff will display all HTML. Full diffs may not be not perfect due to the opening and closing of HTML tags, thus the diff may not perfectly represent the layout of your content. Text Only will strip all HTML tags, including images, which displays the differences in a more basic and straight forward manor.

## Field Diff Settings

<a href="http://docs.boldminded.com/images/diff-settings-field.png" class="fancybox"><img src="http://docs.boldminded.com/images/diff-settings-field.png" width="600" /></a>
Publisher also provides a way to render a diff of each specific field on the publish page. The following settings will appear at the bottom of the field settings page (the Publisher Accessory must be enabled).

### Diff Style
Optionally override the global style setting on a per field basis.

### Snippet
For more complicated fieldtypes, such as Grid, Relationships, or Assets you may need to provide better context for the diff parser to work. Essentially these add-ons use their own tag markup to parse the data, which you need to provide. This setting lets you use an existing snippet file to parse the data. Do <i>not</i> include the channel entries tag inside of these snippets. It is recommended to keep this snippet code a simple as possible and only add what is necessary to view a difference in content. For example do not add superfluous HTML or CSS.

### Custom Template
Instead of using a snippet you can define the tag markup directly on the field settings page. You do not need to include the channel entries tag, only tag necessary to parse the field's contents.

>>> The Snippet and Custom Template settings are only required for displaying diffs in the CP. Displaying diffs on the front-end of your site use your existing templates.

It is recommended to add the following styles, or something similar, to the front-end of your site to see the differences in the markup.

```
.publisher-diff del,
.diff-html-removed,
.diffdel {
    text-decoration: line-through;
    color: red;
}
.publisher-diff ins,
.diff-html-added,
.diffins {
    text-decoration: none;
    color: green;
}
```