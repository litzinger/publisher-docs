>>> Diffs have not been added in Publisher 2 yet. This document describes the functionality found in Publisher 1.

Publisher provides content diffs to show which content has been changed in your drafts. This feature is available in several configurations and options. A diff is a comparison of the open/published version of your content to the draft version. The draft is considered the newest revision, thus diffs are only available when viewing an draft, either in the control panel or the front-end of your site.

Content diffs are not currently available for phrases or categories.

<a href="http://boldminded.com/assets/images/uploads/publisher-diff-example.png" class="fancybox"><img src="http://boldminded.com/assets/images/uploads/publisher-diff-example-sm.png" class="float_right" /></a>
Publisher comes packaged with the Diff library and is the default library which is feature rich and provides fairly accurate diffs, however, there is a what I consider a more robust diff library that is released under a GPL license, thus it can not be packaged with Publisher. I recommend downloading and using this library instead.

<a href="http://boldminded.com/assets/publisher/htmldiff.zip">Download HTML Diff</a> and place the the ``htmldiff`` folder into your ``/third_party/publisher_drivers/`` folder.

Once installed you will need to enable Diffs in the Publisher settings page, and select which driver to use. Diffs can be enabled or disabled on your entry publish page and the front-end of your site, and you can optionally provide a text only diff. Running a diff on HTML content is very complicated unless done on a line by line basis. Opening and closing HTML tags are difficult to track, especially when text around them has changed. For this reason <i>do not</i> expect a perfect diff of your content. Added and removed text will be displayed, but an opening or closing HTML tag may appear in an incorrect location, thus causing the display of the diff to appear slightly different than your actual content. This feature is provided to a diff of the <i>text</i> so your content editors know what has changed.

## Global Diff Settings

The following global settings are available to configure Diffs in the Publisher Settings page.

### Diff Driver
As mentioned above, select which driver/library to use to parse the diffs.

### Diff Enabled (front-end)
Show content diffs on the front-end of your site when viewing a draft? Requires ``?status=draft`` in the URL. Use the <a href="https://boldminded.com/add-ons/publisher/template-tags">Publisher Toolbar</a> to toggle between Published and Draft content.

### Diff Enabled (CP)
Show content diffs next to each field on the publish page in the CP.

### Diff Style
A Full diff will display all HTML. Full diffs are not perfect due to the opening and closing of HTML tags, thus the diff may not perfectly represent the layout of your content. Text Only will strip all HTML tags, including images, which displays the differences in a more basic and straight forward manor.

## Field Diff Settings

<a href="http://boldminded.com/assets/images/uploads/publisher-field-diff-settings.png" class="fancybox"><img src="http://boldminded.com/assets/images/uploads/publisher-field-diff-settings-sm.png" class="float_right" width="200" /></a>
Publisher also provides a way to render a diff of each specific field on the publish page. The following settings will appear at the bottom of the field settings page (the Publisher Accessory must be enabled).

### Enabled
Enable or disable content diff for the field. If no further settings are defined a simple string comparison will be performed on the field text. For text, textarea, or WYSIWYG fields this may be the only setting necessary.

### Diff Style
Optionally override the global style setting on a per field basis.

### Snippet
For more complicated fieldtypes, such as Matrix, Playa, GMaps or Assets you may need to provide better context for the diff parser to work. Essentially these add-ons use their own tag markup to parse the data, which you need to provide. This setting lets you use an existing snippet file to parse the data. Do <i>not</i> include the channel entries tag inside of these snippets.

### Custom Template
Instead of using a snippet you can define the tag markup directly on the field settings page. You do not need to include the channel entries tag, only tag necessary to parse the field's contents.

>>> The Snippet and Custom Template settings are only required for displaying diffs in the CP. Displaying diffs on the front-end of your site use your existing templates.

It is recommended to add the following styles, or something similar, to the front-end of your site to see the differences in the markup.

```
.diff-html-added { color: green; }
.diff-html-removed { color: red; text-decoration: line-through; }
```