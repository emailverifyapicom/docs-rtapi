Quick Start
===========

This quick start guide is designed to get you up and running as fast as possible.

Please follow the steps below in sequence:

1) Get a License Key
--------------------
`Request a trial key <https://api.emailverifyapi.com/GetLicense>`_.


2) Try it!
----------
Plug your license key into the following 

::

	https://api.emailverifyapi.com/api/a/v1?key=INSERTYOURLICENSEKEY&email=test@tester.com
	
Paste the url above into your browser and watch the response come back as follows:

::

	{
		"status":"Bad",
		"additionalStatus":"MailboxDoesNotExist",
		"emailAddressProvided":"test@tester.com",
		"emailAddressChecked":"test@tester.com",
		"emailAddressSuggestion":""
	}

.. note:: 	Internet Explorer may prompt to download the file instead of simply displaying it on screen. 
			This is a quirk of Internet Explorer and not an issue with the :term:`API`.
			We do not recommend Internet Explorer for testing with the :term:`API`. Instead, use
			Chrome or Firefox - both will display the results on screen correctly!

3) Next Steps
-------------
 * :doc:`configuration`
 * :doc:`integration`			