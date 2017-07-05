---
title: Known Issues & Tips
taxonomy:
    category: docs
---

## Known Issues

- Publisher does not work with the eAccelorator. It causes issues with setting cookies and session data.
- Disable GZIP compression on your server for best results. GZIP can cause issues with some PHP scripts.
- Publisher 2 does not support the Playa or Matrix field types from EE Harbor. If you are upgrading from an EE 2 site you can use the [PlayaMatrixImporter](https://github.com/EllisLab/PlayaMatrixImporter) from EllisLab to migrate Playa fields to Relationships, and Matrix fields to Grid.

## Tips

- If using URL Prefix or Translated URLs, and you’re using the Channel URL, Comment Page URL, and Search Results URL settings then do not use a hard-coded domain name as part of the URL. For example, don’t use ``http://site.com/blog/``. Instead, use ``/blog/`` or ``/blog``.
Use a full domain name as the Site URL setting in your config.php file or in ***Admin > General Configuration***. Do not use ``/`` as the site_url value
- Publisher does not support translation of entry comments.
