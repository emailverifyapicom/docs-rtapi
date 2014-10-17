.. _emailverifyapi: https://api.emailverifyapi.com
.. _Spam Traps: http://en.wikipedia.org/wiki/Spamtrap
.. _Disposable Email Addresses: http://en.wikipedia.org/wiki/Disposable_email_address
.. _integration examples: https://api.emailverifyapi.com/CodeExamples/

Features
========

> 99.9% Service Availability
----------------------------
Fully load balanced and automatic fail-over systems dispersed across multiple data centers in multiple regions deliver enterprise grade resilience.

Fanatical Service Quality Management (SQM)
------------------------------------------
`emailverifyapi`_ operational staff obsesively monitor services to ensure the best possible uptime and coverage.

Uptime and functional correctness is actively monitored on a minute by minute basis from multiple data centers dispersed across North America and Europe.

Multi Factor Verification
-------------------------
Progressive verification using multiple verification processes including:

 * Syntax checking
 * DNS checking
 * Mailbox checking
 
Unrivalled Coverage
-------------------
With more than 5 years experience and the benefit of owning our own software stack, emailverifyapi.com has refined its services over the years to provide good coverage not only of the easier B2B domains but also the more techically tricky B2C domains including:
 * Hotmail
 * Yahoo
 * AOL
 * Yandex
 
Unrivalled Integration
----------------------
REStful endpoints integrate with pretty much anything these days. emailverifyapi.com not only supports server to server integration over REST but server to client integration with full support for Cross Origin Resource Scripting (CORS). CORS is available in most modern web browsers and allows rich, client side development using only HTML and JavaScript (jQuery or AngularJS recommended).

See `integration examples`_ for tested integration examples using a wide range of languages including PHP, Java, .NET, jQuery and AngularJS).

Spam Trap Detection
-------------------
After many years R&D, we have developed various “secret sauces” that can effectively detect and eliminate spam traps from several well known block lists.

Disposable Email Address Detection
----------------------------------
Detect and eliminate DEAs.

Unrivalled Performance
----------------------
Strategic data centers in North America and Europe, aggressive caching and cloud based auto-scaling deliver outstanding performance. Typical queries are answered between 0.2 to 1.5 seconds.

API Based Email Verification
----------------------------
Every plan includes authentication systems based on domain Access Control Lists (ACL) and key based access.

Domain based ACL authentication is typically used for client script integrations (e.g. jQuery or AngularJS). Domain licenses are tied into a single domain (e.g. www.mydomain.com).

Key based authentication is typically used for server to server integrations.

Error Correction
----------------
No more “fat finger” syndrome! Our API has an optional feature to remove certain invalid characters such as spaces, slashes etc.

Common Typo Handling
--------------------
`emailverifyapi`_ also searches for common typos and suggest alternatives. E.g. jim99@hotmail.cm is more likely to be jim99@hotmail.com so we’ll validate what the user has entered, but provide you with the more likely alternative suggestion too.

On Screen Reporting
-------------------
Every account comes with a secure online portal for customers to view their current and historic usage via simple, user friendly donut charts.

Thoughtful Versioning
---------------------
Endpoints are “versioned”. This means that emailverifyapi.com can continue to release new functionality without “breaking” existing clients commited to integrating with our systems on legacy endpoints.

What is does
------------
`emailverifyapi`_ is used to check email addresses in real-time. Not only are syntax and domain checked, but that the user mailbox is available too. This is the only way to know for sure if an email address is valid.

Additionally identified as part of the email verification process is extra information including:

* `Disposable Email Addresses`_.
* `Spam Traps`_.


How it does it
--------------
Email addresses are verified using various filters and processes. As a high level overview, an email address submitted for verification goes thorough the following filters:

+---------------+---------------------+---------------------------------+---------------------------------------------------------------------+
| Filter Name	| Example Pass        | Example Fail                    | Why it Failed                                                       |
+===============+=====================+=================================+=====================================================================+
| Syntax        | me@xyzabc.com       | me.xyzabc.com                   | me.xyzabc.com is not a valid email address format                   |
+---------------+---------------------+---------------------------------+---------------------------------------------------------------------+
| DNS A         | post@xyzabc.com     | post@xyzabcNO_DNS_A_RECORD.com  | domain has no DNS A record.                                         |
+---------------+---------------------+---------------------------------+---------------------------------------------------------------------+
| DNS MX        | post@xyzabc.com     | post@xyzabcNO_DNS_MX_RECORD.com | domain has no MX records meaning that domain has no mail server(s). |
+---------------+---------------------+---------------------------------+---------------------------------------------------------------------+
| MailBox       | post@xyzabc.com     | postNoMailBox@xyzabc.com        | Mail box does not exist on the mail server.                         |
+---------------+---------------------+---------------------------------+---------------------------------------------------------------------+

