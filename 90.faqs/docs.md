## How do I set the default language of an MSM site?
The officially supported method is to use the <a href="https://boldminded.com/add-ons/publisher-language-control">Publisher Language Control</a> extension.

## How do I use sub-domains or multiple top level domains with Publisher?
The officially supported method is to use the <a href="https://boldminded.com/add-ons/publisher-domain-control">Publisher Domain Control</a> extension.

## How does Publisher save its data?
Publisher saves most of its data to its own custom tables which mimic ExpressionEngine's native ``exp_channel_titles`` and ``exp_channel_data`` tables. Through the use of ExpressionEngine's hooks the data form these tables are used to replace the data from the native tables when displayed on the front-end or within the control panel.

## Does Publisher create duplicate entries for each language?
No. Due to storing its data in its own tables ExpressionEngine is only aware of 1 database row for each entry.

## Does Publisher translate custom field names or Grid columns in the CP?
Publisher will not translate custom field type names, help text, or Grid column titles. Publisher only supports translation of entry content.

## Will Publisher translate entry comments?
No, Publisher does not support translation of entry comments.

