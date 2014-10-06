.. Real Time Email Verification API documentation master file, created by
   sphinx-quickstart on Sat Oct  4 17:18:36 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Email Verification API
======================

Contents:

.. toctree::
   :maxdepth: 2

`emailverifyapi`_ solves the challenging problem of how to validate and verify email addresses in near real time.

.. _emailverifyapi: https://api.emailverifyapi.com
.. _Github: https://github.com/emailverifyapicom/docs-rtapi
.. _Integration Examples: https://api.emailverifyapi.com/CodeExamples
.. _Disposable Email Addresses: http://en.wikipedia.org/wiki/Disposable_email_address
.. _Spam Traps: http://en.wikipedia.org/wiki/Spamtrap

Features
--------
What is does
~~~~~~~~~~~~
`emailverifyapi`_ is used to check email addresses in real-time. Not only are syntax and domain checked, but that the user mailbox is available too. This is the only way to know for sure if an email address is valid.

Additionally identified as part of the email verification process is extra information including:

* `Disposable Email Addresses`_.
* `Spam Traps`_.


Possible applications for the email verification API
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* If you operate a lead generation web site, blog or forum make it harder for users to sign up with false emails.
* For e-commerce checkouts, make sure customers receive their order notifications by preventing invalid emails from being entered.
* If your call centre takes email addresses as part of the customer contact data, real-time verification can greatly reduce the amount of incorrectly keyed emailed addresses.
* For software vendors where email addresses are captured as part of the on-boarding process, integrate full email verification as a value-add for your service.
* With `emailverifyapi`_, there is no need any more to take incorrect email addresses and wait for them to bounce!


How it does it
~~~~~~~~~~~~~~
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



Installation
------------
There is no software to install. `emailverifyapi`_ is Software as a Service exposed as a simple RESTful service that is available to anything connected to The Internet.

Configuration
~~~~~~~~~~~~~
There is nothing to configure.

Integration
~~~~~~~~~~~
There are comprehensive `Integration Examples`_ showing diverse examples of server and client languages.


Contribute
----------
* Contribute to documentation @ `Github`_.

 

 
Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`