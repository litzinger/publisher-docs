---
title: Installation
taxonomy:
    category: docs
---

>>> You must upgrade to the latest version of Publisher by clicking the Run Module Updates button in ExpressionEngine 2 before upgrading to ExpressionEngine 3. Failure to do this will void any support tickets you may have resulting from a failed upgrade. The latest version of Publisher 1 is included in your Publisher 2 zip file.

To install Publisher move the ``/addons/publisher/`` directory to your ``/system/user/addons/`` folder. Also copy the ``/themes/user/publisher/`` folder to the ``/themes/user/`` directory in your ExpressionEngine install. Login to your control panel and visit the Developer > Add-on Manager page, and click the Install link for Publisher.

>>> If your are installing Publisher on an existing site which contains more than 50 entries you will be prompted to continue to step 2 of the installation process. From there Publisher will continue its installation process by migrating the existing entries into Publisher's database tables.

After installation you will be directed to the ***Publisher > Languages*** management page. Publisher requires at least 1 language to be present at all times, and installs with English as the default language. You can change the default language by either adding additional languages and identifying one of them as the default, or by editing English and changing its long name and short name values to another language. Changing the long and short name values are recommended if your site’s default language will not be English. During the install process all existing entries are assigned the language ID of “1”, assuming your existing entries at the time of install are in your default language, you will want to change the long and short name values of “English” to your default language name, thus keeping the language ID values properly assigned to your entries.

If you add no additional languages Publisher will not show a language drop down menu in the toolbar, thus Publisher will only let you create drafts and published versions of content, no translations.

<iframe src="https://player.vimeo.com/video/224449175" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/224449175">Publisher 2 Installation</a> from <a href="https://vimeo.com/user4788348">Brian Litzinger</a> on <a href="https://vimeo.com">Vimeo</a>.</p>