.. _email-checker.com: https://www.email-checker.com/email-checker-api/

Configuration And Usage
=======================

Authentication
--------------
Each call to the :term:`API` must be authenticated. Authentication with the API is performed by either:

 * :term:`ACL`.
 * :term:`License Key`.

Accessing the API using key authentication
------------------------------------------
Access the :term:`API` at::

	https://api.email-checker.com/api/a/v1?key=yourapikey&email=test@tester.com
	
Sending the following parameters :-

.. 	_figure1:

Figure 1 - REST Request Variables
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
+-----------+---------------------------------------------------------+----------+
| Parameter | Value                                                   |          |
+===========+=========================================================+==========+
| key       | your unique API key supplied by us                      | required |
+-----------+---------------------------------------------------------+----------+
| email     | the email address to be validated                       | required |
+-----------+---------------------------------------------------------+----------+
| correct   | **1** - this will remove certain invalid characters.    | optional |
|           |                                                         |          |
|           | **0** - this will leave the email untouched.            |          |
+-----------+---------------------------------------------------------+----------+

.. note:: Need a license key? `Click here <https://www.email-checker.com/email-checker-api/#trial_key>`_.

Accessing the API using ACL authentication
------------------------------------------

::

	https://api.email-checker.com/api/b/v1?email=test@tester.com

.. note:: For :term:`ACL` based authentication, it is not necessary to include the license key in the request. Other parameters (e.g. 'correct') are supported as in the key based example as in :ref:`figure1`.

Responses
---------

.. note:: For a full definition of possible responses, see :doc:`status-codes`.

You will receive back the following values in the response.

Figure 2 - Responses
^^^^^^^^^^^^^^^^^^^^
+------------------------+---------------------------------------------------------------------------------------------+------------------------+
| Response               | Description                                                                                 | Example values         |
+========================+=============================================================================================+========================+
| status                 | The validation result                                                                       | 'Ok', 'Bad', 'Unknown' |
+------------------------+---------------------------------------------------------------------------------------------+------------------------+
| additionalStatus       | Additional information for BAD and UNKNOWN results                                          | NoMxServersFound       |
+------------------------+---------------------------------------------------------------------------------------------+------------------------+
| emailAddressProvided   | The exact email address passed to the API including obvious typos and errors                | test@tester.com        |
+------------------------+---------------------------------------------------------------------------------------------+------------------------+
| emailAddressChecked    | The actual email address validated                                                          | test@tester.com        |
+------------------------+---------------------------------------------------------------------------------------------+------------------------+
| emailAddressSuggestion | A suggested alternative if a common typo was noticed e.g. if 'fred@hotmail.cm' was provided | fred@hotmail.com       |
+------------------------+---------------------------------------------------------------------------------------------+------------------------+

.. note:: Example response for email address *test@tester.com*

The URL passed to the API is :-

::

	https://api.email-checker.com/api/a/v1?key=yourapikey&email=test@tester.com

The response would be :-

::

	{
	"status":"Bad",
	"additionalStatus":"MailboxDoesNotExist",
	"emailAddressProvided":"test@tester.com",
	"emailAddressChecked":"test@tester.com",
	"emailAddressSuggestion":""
	}

The 'correct' Parameter
-----------------------
Optionally, you can also use the 'correct' parameter to remove certain invalid characters such as spaces, slashes, square brackets etc. Example using the 'correct' parameter. The user enters an email address *john99]@gmail.com* Here is the API call that would be made :-

::

	http://api.email-checker.com/api/a/v1?key=yourapikey&email=john99]@gmail.com&correct=1

`email-checker.com`_ will automatically remove the invalid character ']' and send the corrected version through for validation. Example results based on the above API call :-

::

	{
	"status":"Ok",
	"additionalStatus":"None",
	"emailAddressProvided":"john99]@gmail.com",
	"emailAddressChecked":"john99@gmail.com",
	"emailAddressSuggestion":""
	}
	
Additional Status Information
-----------------------------
When an email address is returned with a status of *Bad* or *Unknown* we return the detailed reason as part of the response in the *additionalStatus* value. For a full list of additional status values, please refer to :doc:`status-codes`.

Sandbox
-------
A sandbox environment is available to assist customers with testing, evaluation and integration. The sandbox url is:

::

	https://api.email-checker.com:443/api/a/v1/sandbox
	
There is no charge for use and your live quota is not affected. No emails are verified in the sandbox and responses are hard coded.

For a full list of hard coded test cases, please see `here <https://docs.google.com/spreadsheets/d/11GPGePUcE9fZAd4L8qKLeoB1mWhWXoiueCdgVgitiKQ/edit?usp=sharing>`_.

Firewall
--------
If you need to enable firewall rules based on IP addresses, you will need to add the following addresses, for ports 80 and 443, to your firewall rules:
 * 23.96.209.155
 * 23.98.64.158
 * 191.235.208.12
 * 137.117.224.218