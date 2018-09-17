Frequently Asked Questions
==========================

Feature X was available in Miniflux 1?
--------------------------------------

Miniflux 2 doesn't try to reimplement all features of Miniflux 1.
The minimalist approach is pushed a little bit further.

If you really miss something, **you must contribute to the project**, but remember, **you have to keep the minimalist philosophy of Miniflux**.

Why are you not developing my feature request?
----------------------------------------------

- Developing a software takes a lot of time.
- This is a free and open source project, no one owes you anything.
- If you miss something, contribute to the project.
- Don't expect anyone to work for free.
- As mentioned above, the number of features is voluntarily limited. Nobody likes bloatware.
- Improving existing features is more important than adding new ones.

Why Miniflux stores favicons into the database?
-----------------------------------------------

Miniflux follows the `the Twelve Factors principle <https://12factor.net/>`_.
Nothing is stored on the local file system.
The application is designed to run on ephemeral containers without persistent storage.

How to create themes for Miniflux 2?
------------------------------------

As of now, Miniflux 2 doesn't have any mechanism to load external stylesheets to avoid dependencies.
Themes are embedded into the binary.

If you would like to submit a new official theme, you must send a pull-request.
But do not forget that **you will have to maintain your theme over the time**, otherwise, your theme will be removed from the code base.

Why there is no plugin system?
------------------------------

- Because this software has a minimalist approach.
- Because implementing a plugin system increase the complexity of the software.
- Because people do not maintain their plugins after a while.

What is "Save this article"?
----------------------------

"Save" sends the feed entry to third-party services like Pinboard or Instapaper if configured.

How are items removed from the database?
----------------------------------------

When a subscription is refreshed, entries marked as "removed" and not visible anymore in the XML feed are removed from the database.

What "Flush History" does?
--------------------------

"Flush History" changes the status of entries from "read" to "removed" (except for bookmarks).
Entries with the status "removed" are not visible in the user interface.

Is there any browser extensions for Miniflux?
---------------------------------------------

- Miniflux Notifications: `Chrome Web Store <https://chrome.google.com/webstore/detail/miniflux-notifications/jpeplhckmjlpahnkpblakfligkbfefkg>`_ - `Source Code <https://github.com/modInfo/miniflux-chrome-notifier>`_

Which binary do I need to use on my Raspberry Pi?
-------------------------------------------------

+---------------------+-----------------------+
| Raspberry Pi Model  | Miniflux Binary       |
+=====================+=======================+
| A, A+, B, B+, Zero  | miniflux-linux-armv6  |
+---------------------+-----------------------+
| 2 and 3             | miniflux-linux-armv7  |
+---------------------+-----------------------+

Which binary do I need to use on Scaleway ARM machines?
-------------------------------------------------------

+----------------+-----------------------+----------+
| Server Type    | Miniflux Binary       | uname -m |
+================+=======================+==========+
| Scaleway C1    | miniflux-linux-armv6  |  armv7l  |
+----------------+-----------------------+----------+
| Scaleway ARM64 | miniflux-linux-armv8  |  aarch6  |
+----------------+-----------------------+----------+

Which Docker architecture should I use?
---------------------------------------

Pulling the ``latest`` tag or a specific version should download the correct image according to your machine.

+---------------------+----------+----------------+
| Docker Architecture | uname -m | Example        |
+=====================+==========+================+
| amd64               |  x86_64  |                |
+---------------------+----------+----------------+
| arm32v6             |  armhf   | Raspberry Pi   |
+---------------------+----------+----------------+
| arm32v6             |  armv7l  | Scaleway C1    |
+---------------------+----------+----------------+
| arm64v8             |  aarch6  | Scaleway ARM64 |
+---------------------+----------+----------------+

If you use the wrong architecture, Docker will returns an error like this one: ``standard_init_linux.go:178: exec user process caused "exec format error"``.

.. note:: Multi-arch Docker images are available only since Miniflux v2.0.12

Why SQL migrations are not executed automatically?
--------------------------------------------------

- Because it's a source of problems.
- Only one process should manipulate the database schema at once.
- If you run multiple containers with an orchestrator that may cause issues.
- You can still run the migrations by defining the variable ``RUN_MIGRATIONS=1``.
