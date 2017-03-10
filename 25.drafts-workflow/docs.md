---
title: Drafts & Workflow
taxonomy:
    category: docs
---

To view a draft on the front-end, just add ``?publisher_status=draft`` to your URL, or use the ``{exp:publisher:toolbar}`` tag, which will add links to toggle the page status.

## Draft Publish Previews

Publisher includes draft publish previews. When saving an entry as a draft you will be redirected to the default ExpressionEngine entry preview page, which is normally not very helpful. With draft previews enabled, the entry you published will be viewable within the context of your site. Structure managed pages are handled automatically, but additional configuration may be required to view non-Structure managed entries, or entries that may appear only within a listing of other entries. To manage these previews Publisher has a Preview Templates settings page where you can select a template to use as the preview template. You can optionally append the new ``entry_id``, ``url_title``, or custom segments to the end of the preview template, thus enabling custom preview templates. This is designed to require minimal to no changes in your templates to preview drafts.

## Authorized Draft Previews

As of version 1.5, draft previews can optionally include a secret key that prevents anonymous previewing of drafts if a user adds ``?publisher_status=draft`` to the URL. Authorized previews are valid only on the same domain name the entry was saved in. The draft approval emails contain a ``{preview_url}`` variable that can be used to notify non-EE users that a draft is available. Users without CP access cannot approve the draft.

## Toolbar

When viewing a draft the toolbar will have a yellow background. This is so content editors are aware of the fact that they are working on a draft.

The toolbar does not include a button for "Save As Draft" and "Publish" at the same time. This is a very conscience design decision. While it might take an extra click for your content editors to save a piece of content, that extra click requires the editor to think about what they are doing instead of accidently smashing the wrong button. There is also a technical reason for it. Publisher has several hooks in which you can alter the functionality of the toolbar. One of these hooks lets you add to or alter save options. All options must have a save value as "open" or "draft", but you can change the labels of these values. Such functionality should let developers create more workflow options on top of Publisher with their own add-on. If this hook added multiple buttons intead of save statuses it would become visually overwhelming and confusing.

## Draft Status

![Toolbar in Draft mode](http://docs.boldminded.com/images/toolbar-draft.png)

Publisher does not hi-jack the native Status field. You are still free to use it however you like. The "Save As" option in the Publisher toolbar should be thought of as a state rather than a status. Entries can be in a Draft or Published state, but still retain any custom entry statuses, thus you are free to use statuses such as "Hidden in nav." If you are creating a new entry and save it in the Draft state, and a Draft status option does not exist in the channel you are editing it will create a Draft status option, thus the new entry will not appear on your live site until you set it to Open or save the entry as Published. Separating the default status menu with the Publisher statuses gives you more control over the display of your entries. The Publisher's Draft and Published states are strictly for Publisher and the approval process. With this separation you can easily hide an entry on your site entirely by setting the native Status field to "Closed." The entry will not display in any ``{exp:channel:entries}`` loops and the Publisher states will be unchanged.

When previewing drafts be sure to add the ``status="{publisher:entry_status}"`` parameter to your entry tags. See the Template Tags docs for more information.