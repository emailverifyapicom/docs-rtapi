
.. _Detailed Response Codes:

Email Verification Response Codes For API V1
============================================

.. _Main Status Response Codes:

Main Status Response Codes
--------------------------
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
-----------------------
:None:
	No additional information is available.
	
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
