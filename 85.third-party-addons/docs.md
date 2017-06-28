---
title: Third Party Add-ons
taxonomy:
    category: docs
---

# Structure
Publisher does not support the trailing slash in site pages which was dropped in EE around version 2.5, however, Structure has a backwards compatibility setting to keep the trailing slashes, but this is not supported by Publisher. You must disable the use of trailing slashes in Structure to maintain Publisher compatibility.

## Structure Tags
The following parameters will need to be added to Structure tags to work with Publisher.

    {exp:structure:titletrail channel:title="publisher"}
    {exp:structure:breadcrumb channel:title="publisher"}

You may need to add this parameter to the structure:breadcrumb tag in order for it to work properly due to a bug in Structure.

    rename_home=”{structure:top:title}”

In most cases the `start_from` parameter will work just as you expect it to when using translated URLs. For example `start_from=”{segment_1}”`. However, for the cases in which you need to start the navigation from a page other than the page the user is currently on you will need to use `{page_uri:XX}`, where XX is the entry ID of the page you want the navigation to start from. Normal segment variables or string values will not work in this case because Publisher does not know the translated value or depth of the URL of page you are requesting the navigation to start from. The parameter will end up as `start_from=”{page_uri:123}”`.

All Structure global variables will be updated with the translated values as well.

    {structure:top:title}
    {structure:parent:title}
    {structure:page:title}
    {structure:top:url}
    {structure:parent:url}
    {structure:page:url}
    {structure:top:uri}
    {structure:parent:uri}
    {structure:page:uri}
    {structure:top:slug}
    {structure:parent:slug}
    {structure:page:slug}


# Channel Form
To enable support for Channel Form, you need to add 3 hidden fields to your forms:

    <input type="hidden" name="publisher_save_status" value="draft|open" />
    <input type="hidden" name="publisher_view_status" value="draft|open" />
    <input type="hidden" name="lang_id" value="{publisher:current_language_id}" />

To send approval notification emails when submitting a Channel Form, add this hidden field to the form.

    <input type="hidden" name="send_approval" value="y" />

If you wish to let users edit a draft version of an entry while the rest of the page is displaying Open/Published content, add this parameter to the Safecracker tag:

    {exp:channel_form:form publisher_status="draft"}


# Low Seg 2 Cat
If you are currently using Low Seg 2 Cat and are using translated URLs in Publisher, then you might want to try [URL Helper](https://github.com/litzinger/URL-Helper) instead. It works specifically with Publisher and provides nearly identical functionality as Low Seg 2 Cat (plus more) and will return the category segment values even with translated URLs.