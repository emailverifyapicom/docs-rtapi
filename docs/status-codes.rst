
.. _Detailed Response Codes:

Email Verification Response Codes For API V1
============================================
A response is a message consisting of a standard :term:`HTTP` header and body. 
The body of the message contains the detail of the message (e.g. the :term:`JSON` data with email verification detail). 
The header of the message contains general :term:`HTTP` information such as :term:`HTTP` status codes.

**Response Body Content**

 * `Main Status Response Codes`_
 * `Additional Status Codes`_
 
**Response Header**

 * `HTTP Status Codes`_


Response Body Content
---------------------

.. _Main Status Response Codes:

Main Status Response Codes
^^^^^^^^^^^^^^^^^^^^^^^^^^
:Ok:
	Verification passes all checks including Syntax, :term:`DNS`, 
	:term:`MX`, Mailbox, Deep Server Configuration, :term:`Grey Listing`

:Bad:
	Verification fails checks for definitive reasons (e.g. mail box does not exist)
	
:Unknown:
	Conclusive verification result cannot be achieved due to mail server configuration 
	or anti-spam measures. See table \"Additional Status Codes\".

.. _Additional Status Codes:
	
Additional Status Codes
^^^^^^^^^^^^^^^^^^^^^^^
:None:
	No additional information is available. 
	
	This status differs from a TransientNetworkFault as it should not be retried 
	(the result will not change).
	
	There are a few known reasons for this status code for example the target mx record uses 
	:term:`Office 365` or a mail provider implementing custom mailbox shutdowns.
	
:AtSignNotFound:
	The required '@' sign is not found in email address.

:DomainIsInexistent:
	The domain (i.e. the bit after the '@' character) defined in the email address 
	does not exist, according to :term:`DNS` records.

	A domain that does not exist cannot have email boxes. A domain that does not 
	exist cannot have email boxes.

:DomainIsWellKnownDea:
	The domain is a well known Disposable Email Address :term:`DEA`.

	There are many services available that permit users to use a one-time 
	only email address. Typically, these email addresses are used by 
	individuals wishing to gain access to content or services requiring 
	registration of email addresses but same individuals not wishing to 
	divulge their true identities (e.g. permanent email addresses).

	:term:`DEA` addresses should not be regarded as valid for email 
	send purposes as it is unlikely that messages sent to :abbr:`DEA(Disposable Email Address)` 
	addresses will ever be read. :abbr:`DEA(Disposable Email Address)` 
	addresses should not be regarded as valid for email send purposes 
	as it is unlikely that messages sent to :term:`DEA` addresses will ever be read.
	
:MailboxFull:
	The mailbox is full.

	Mailboxes that are full are unable to receive any further email 
	messages until such time as the user empties the mail box or the 
	system administrator grants extra storage quota.

	Most full mailboxes usually indicate accounts that have been 
	abandoned by users and will therefore never be looked at again.

	We do not recommend sending emails to email addresses identified 
	as *full*.
	
:MailboxDoesNotExist:
	The mailbox does not exist.
	
	100% confidence that the mail box does not exist.
	
:NoMxServersFound:
	There are no mail servers defined for this domain, according to :term:`DNS`.
	
	Email addresses cannot be valid if there are no email servers 
	defined in :term:`DNS` for the domain.
	
:ServerDoesNotSupportInternationalMailboxes:
	The server does not support international mailboxes.
	
	International email boxes are those that use international 
	character sets such as Chinese / Kanji etc.
	
	International email boxes require systems in place for :term:`Punycode` 
	translation.

	Where these systems are not in place, email verification or delivery 
	is not possible.
	
	For further information see :term:`Punycode`.
	
:ServerIsCatchAll:
	The server is configured for *catch all* and responds to all 
	email verifications with a status of *Ok*.

	Mail servers can be configured with a policy known as *Catch All*. 
	Catch all redirects any email address sent to a particular 
	domain to a central email box for manual inspection. Catch all 
	configured servers cannot respond to requests for email address verification.
	
:Success:
	Successful verification.
	
	100% confidence that the mail box exists.
	
:TooManyAtSignsFound:
	Too many '@' signs found in email address.

	Only one '@' character is allowed in email addresses.
	
:Unknown:
	The reason for the verification result is unknown.
	
:TransientNetworkFault:
	A temporary network fault occurred during verification. Please try again later.

	Verification operations on remote mail servers can sometimes fail for a number 
	of reasons such as loss of network connection, remote servers timing out etc.
	
	One other possible cause of a temporary fault is :term:`Grey Listing`.

	These conditions are usually temporary. Retrying verification at a later time 
	will usually result in a positive response from mail servers.
	
	Please note that setting an infinite retry policy around this status code is 
	inadvisable as there is no way of knowing when the issue will be resolved within 
	the target domain or the grey listing resolved, and this may affect your daily quota.

:PossibleSpamTrapDetected:
	A possible spam trap email address or domain has been detected.

	Spam traps are email addresses or domains deliberately placed on-line 
	in order to capture and flag potential spam based operations.

	Our advanced detection heuristics are capable of detecting likely 
	spam trap addresses or domains known to be associated with spam trap techniques.

	We do not recommend sending emails to addresses identified as associated 
	with known spam trap behaviour.

	Sending emails to known spam traps or domains will result in your :term:`ESP` 
	being subjected to email blocks from a :term:`DNS` :term:`Block List`..

	An :term:`ESP` cannot tolerate entries in a :term:`Block List` (as it adversely 
	affects email deliver-ability for all customers) and will actively refuse 
	to send emails on behalf of customers with a history of generating entries in a :term:`Block List`.

	
Response Header
---------------

..	_HTTP Status Codes:

HTTP Status Codes
^^^^^^^^^^^^^^^^^
In additional to the application level codes (see `Main Status Response Codes`_ and `Additional Status Codes`_) 
returned in the :term:`HTTP` message body, :term:`HTTP` status codes are returned in the :term:`HTTP` header.

:200:
	Call successful.
	
:304:
	The cached copy on the client is up to date. Resource not transferred. Use this with client side 
	"If-Modified-Since" request for efficient caching. 
	Caching is available for both :term:`HTTP` and HTTPS options.

:400:
	Bad request. The server could not understand the request. Perhaps missing a license key or an email to check?
	Conditions that lead to this error are: No license key supplied, no email address supplied, email address > 255 
	characters, license key in incorrect format.
	
:401:
	Possible reasons: The provided license key is not valid, the provided license key has expired, 
	the provided license key is not permitted for use from this domain, 
	you have reached your quota capacity for this account, 
	this account has been disabled.
	
:500:
	An error occurred on the server. Possible reasons are: license key validation failed or 
	a general server fault.