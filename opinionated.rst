Opinionated?
============

Miniflux is a minimalist software.
The purpose of this application is to read feeds.
*Nothing else*.

Focus on Simplicity
-------------------

- Having a gazillion of features makes the software hard to maintain, hard to troubleshoot and increase the number of bugs.
- This software doesn't try to satisfy the needs of everyone.

Why the user interface is ugly?
-------------------------------

- The Miniflux layout is optimized to scan entries quickly.
- The design of Miniflux is inspired by `Hacker News <https://news.ycombinator.com/>`_, `Lobsters <https://lobste.rs/>`_ and `Pinboard <https://pinboard.in/>`_.

Why are you not developing my feature request?
----------------------------------------------

- Developing a software takes a lot of time. Don't expect anyone to work for free.
- As mentioned above, the number of features is voluntarily limited. Nobody likes bloatware.
- Improving existing features is more important than adding new ones.

Why choose Golang as a programming language?
--------------------------------------------

`Go <https://golang.org/>`_ is probably the best choice for self-hosted software:

- Go is a simple programming language.
- Running code concurrently is part of the language.
- It's faster than a scripting language like PHP or Python.
- The final application is a binary compiled statically without any dependency.
- You just need to drop the executable on your server to deploy the application.
- You don't have to worry about what version of PHP/Python is installed on your machine.
- Packaging the software using RPM/Debian/Docker is straightforward.

Why Postgresql?
---------------

Miniflux is compatible only with Postgres.

- Supporting multiple databases increases the complexity of the software.
- We do not have the resources to test the software with all major versions of MySQL, MariaDB, Sqlite, and so on.
- ORM abstracts some interesting features provided by your database.
- Managing schema migrations with Sqlite is painful.
- Postgresql is powerful, rock solid and battle tested.
- Postgresql is a great independent open source software.
- Miniflux uses *hstore/jsonb/inet* data types, window functions, full-text search and handles user timezones with Postgres.

Why no Javascript framework?
----------------------------

Miniflux uses Javascript only where it's necessary.

- Rendering templates server side is very simple and fast enough for that kind of application.
- Using Javascript frameworks increase complexity.
- The Javascript ecosystem is moving all the time, sticking to the standard is probably more sustainable.
- Having too many dependencies is painful to maintain and update on the long term.

Why only ECMAScript 6?
----------------------

Miniflux uses ES6 and the Fetch API.

- All modern browsers support ES6 nowadays.
- Only Internet Explorer doesn't support ES6, but who cares?
- Using a Javascript transpiler introduce another set of useless dependencies.

Why there is no mobile application?
-----------------------------------

Using the web UI on your smartphone is not so bad:

- Miniflux is a `progressive web app <https://developer.mozilla.org/en-US/Apps/Progressive>`_
- The layout adapts to the screen size (responsive design)
- You could add the application to the home screen like any native application
- You can swipe entries horizontally to change their status
- The web browser is a pretty good sandbox, the application cannot access to the data stored on your phone
- It's cross platform: works on iOS and Android

The development of mobile clients is left to the open source community:

- Developing a native mobile application for each platform (iOS and Android) and different devices (smartphones and tablets) takes a lot of work
- The main developer of Miniflux is not a mobile application developer
- You have to pay a fee to publish your app on the store even if your app doesn't make any money
