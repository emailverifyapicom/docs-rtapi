.. _emailverifyapi.com: https://api.emailverifyapi.com

Frequently Asked Questions
==========================

How can I get a key?
--------------------
Please contact your reseller to request a key. Trial keys are available on request.

How do I call the API?
----------------------
Make a simple GET request to the endpoint. For example, to query email address *anyone@yourdomain.com* with license key *ABCD1234* call:

::
	
	https://api.emailverifyapi.com/api/a/v1?key=ABCD1234&email=anyone@yourdomain.com

	
What comes back from the API?
-----------------------------
A :term:`JSON` based response similar to:

::
	
	{
	"status":"Bad",
	"additionalStatus":"MailboxDoesNotExist",
	"emailAddressProvided":"anyone@yourdomain.com",
	"emailAddressChecked":"anyone@yourdomain.com",
	"emailAddressSuggestion":""
	}

.. note:: For a detailed explanation of response codes, please see :doc:`status-codes`.

How can I integrate the API with my solution?
---------------------------------------------
We have tested, detailed integration examples using a wide range of technologies and languages including Java, PHP, .NET, jQuery and Angular. Please see :doc:`integration` for more information.

How reliable is the API?
------------------------
> 99.9% average availability. See our public `service status page <http://stats.emailverifyapi.com>`_.

Does the system get slower when it's busy?
------------------------------------------
No. All infrastructure is hosted in cloud based platforms with automatic scaling enabled. Automatic scaling kicks in at busy times to provide more hardware resources to meet demand.

Can it do Hotmail?
------------------
Yes.

Can it do Yahoo?
----------------
Yes. Based on our own internal testing `emailverifyapi.com`_ is currently the only email verification service to offer effective and repeatable coverage for Yahoo addresses.

Can it do Yandex?
-----------------
Yes it can.

Can it find spam traps?
-----------------------
Partially.

A :term:`Spam Trap` is a moving target. In theory (and indeed in practice) anyone can setup a :term:`Block List` and start putting spam traps into the wild.

`emailverifyapi.com`_ has :term:`Spam Trap` detection capabilities that covers several of the well known block lists. Whilst it is not possible to deliver 100% coverage of all spam traps from all block lists, `emailverifyapi.com`_ provides the best :term:`Spam Trap` detection capabilities available.

How does it work?
-----------------
At a basic conceptual level, the process of verifying email addresses is very simple. Google for \"Send email using telnet\" for a quick and general overview of how it's done. To verify an email address without sending an email, simply go as far as the \"RCPT TO\" stage and parse the response code. That's the easy bit and can be accomplished in just a couple of dozen lines of a PHP script!

The hard bit is dealing with mail services that are intrinsically configured to work against the process of email verification or any similar SMTP based activity. The reason that any email / :term:`SMTP` process is difficult from a client perspective is that mail services need to protect themselves from an ever increasing landscape of abuse including spam and :term:`DDoS` attacks.

`emailverifyapi.com`_'s strength in dealing with the \"hard bit\" of email verification comes from years of experience in doing email verification together with our complete ownership of our :term:`SMTP` verification software stack together with an extensive cloud based infrastructure. That's why `emailverifyapi.com`_ can do the \"hard bits\" best and offer outstanding coverage on the more difficult domains such as Yahoo and Hotmail.

Can I get blacklisted using this API?
-------------------------------------
No. It's `emailverifyapi.com`_ infrastructure that does the work.

Will anyone know that I am verifying their email address?
---------------------------------------------------------
No. It's `emailverifyapi.com`_ infrastructure that does the work.