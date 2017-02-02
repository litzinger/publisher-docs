---
title: Known Issues & Tips
taxonomy:
    category: docs
---

## Known Issues

- Installation can take a few minutes if you are installing into an existing site that has 500+ entries.
- Publisher does not work with the eAccelorator. It causes issues with setting cookies and session data.
- Disable GZIP compression on your server for best results. GZIP can cause issues with some PHP scripts.
- Publisher 2 does not support the Playa or Matrix field types from EE Harbor. EllisLab has created a Playa and Matrix to Relationships and Grid conversion plugin. As of December 2016 Playa and Matrix are not available for EE3. Even if they ever do become available Publisher 2 will never support them. The main reason for this decision is to reduce added complexity to the codebase and reduce the overall support necessary for Publisher.

## Tips

- If using URL Prefix or Translated URLs, and you’re using the Channel URL, Comment Page URL, and Search Results URL settings then do not use a hard-coded domain name as part of the URL. For example, don’t use ``http://site.com/blog/``. Instead, use ``/blog/`` or ``/blog``.
Use a full domain name as the Site URL setting in your config.php file or in ***Admin > General Configuration***. Do not use ``/`` as the site_url value
- Publisher does not support translation of entry comments.
