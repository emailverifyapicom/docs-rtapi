.. _emailverifyapi.com: https://api.emailverifyapi.com
.. _Live Operational Status Page: http://stats.emailverifyapi.com/

Features
========

> 99.9% Service Availability
----------------------------

.. note:: View the `Live Operational Status Page`_ online.

Fully load balanced and automatic fail-over systems dispersed across 
multiple data centers in multiple regions deliver enterprise grade resilience.

Fanatical Service Quality Management (SQM)
------------------------------------------
`emailverifyapi.com`_ operational staff obsessively monitor services to 
ensure the best possible uptime and coverage.

Uptime and functional correctness is actively monitored on a minute by 
minute basis from multiple data centers dispersed across North America and Europe.

Multi Factor Verification
-------------------------
Progressive verification using multiple verification processes including:

 * Syntax checking
 * DNS checking
 * Mailbox checking
 
Unrivalled Coverage
-------------------
With more than 5 years experience and the benefit of owning our own 
software stack, `emailverifyapi.com`_ has refined its services over 
the years to provide good coverage not only of the easier :term:`B2B` 
domains but also the more technically tricky :term:`B2C` domains including:

 * Hotmail
 * Yahoo
 * AOL
 * Yandex
 
Unrivalled Integration
----------------------
:term:`RESTful` endpoints integrate with pretty much anything these 
days. `emailverifyapi.com`_ not only supports server to server 
integration over REST but server to client integration with full 
support for :term:`CORS`. :term:`CORS` is available in most modern 
web browsers and allows rich, client side development using only 
HTML and JavaScript (jQuery or AngularJS recommended).

See :doc:`integration` for tested integration examples using a wide 
range of languages including PHP, Java, .NET, jQuery and AngularJS).

Spam Trap Detection
-------------------
After many years R&D, `emailverifyapi.com`_ has developed various \"secret sauces\" 
that can effectively detect and eliminate spam traps from several well known :term:`Block List`.

Disposable Email Address Detection
----------------------------------
Detect and eliminate :term:`DEA`.

Unrivalled Performance
----------------------
Strategic data centers in North America and Europe, aggressive 
caching and cloud based auto-scaling deliver outstanding performance. 
Typical queries are answered between 0.2 to 1.5 seconds.

.. note:: See :doc:`technical-spec`

API Based Email Verification
----------------------------
Every plan includes authentication systems based on :term:`ACL` 
and :term:`License Key` based access.

Domain based :term:`ACL` authentication is typically used for 
client script integrations (e.g. jQuery or AngularJS). 
Domain licenses are tied into a single domain (e.g. www.mydomain.com).

:term:`License Key` based authentication is typically used for 
server to server integrations.

Error Correction
----------------
No more \"fat finger\" syndrome! Our :term:`API` has an optional 
feature to remove certain invalid characters such as spaces, slashes etc.

Common Typo Handling
--------------------
`emailverifyapi.com`_ also searches for common typos and suggest 
alternatives. E.g. jim99@hotmail.cm is more likely to be jim99@hotmail.com 
so `emailverifyapi.com`_ will validate what the user has entered, 
but provide you with the more likely alternative suggestion too.

On Screen Reporting
-------------------
Every account comes with a secure online portal for customers to 
view their current and historic usage via simple, user friendly donut charts.

Thoughtful Versioning
---------------------
Endpoints are \"versioned\". This means that `emailverifyapi.com`_ 
can continue to release new functionality without \"breaking\" 
existing clients committed to integrating with our systems on legacy endpoints.

What is does
------------
`emailverifyapi.com`_ is used to check email addresses in real-time. 
Not only are syntax and domain checked, but that the user mailbox 
is available too. This is the only way to know for sure if an email address is valid.

Additionally identified as part of the email verification process 
is extra information including:

* :term:`DEA`.
* :term:`Spam Trap`.


How it works
------------
Email addresses are verified using various filters and processes. 
As a high level overview, an email address submitted for verification 
goes thorough the following filters:

Syntax
	A basic inspection of the systax of the email address to see 
	if it looks valid. Work is done only using server :abbr:`CPU(Central Processing Unit)` 
	based on simple pattern matching algorithms.
	
DNS A
	Verifies a domain exists in :term:`DNS`. Domains that do not 
	exist in :term:`DNS` cannot have mail servers or email boxes.
	
	:term:`DNS` checks are performed over the network.
	
DNS MX
	Verify :term:`MX` records using :term:`DNS`. Domains that do not have 
	:term:`MX` records, have no mail servers and therefore no valid email boxes.
	
	:term:`MX` checks are performed over the network.

MailBox
	Verify email boxes with :term:`SMTP` checks.
	
	Connect to mail server and perform :term:`SMTP` 
	protocol to verify if mail box exists.
	
	This is the deepest level of verification. It is 
	performed over the network.
	