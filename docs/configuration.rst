Configuration And Usage
=======================

.. _emailverifyapi: https://api.emailverifyapi.com
.. _Detailed Response Codes: https://drive.google.com/file/d/0B0ODsJFfpng0aDJLb2hKVWZnbm8/view?usp=sharing

Authentication
--------------
Each call to the API must be authenticated. Authentication with the API is performed by either:

 * :abbr:`ACL(Access Control List)`. ACL is checked against the domain calling the API. ACL authentication does not require a license key and is best in situations where the API is being called from client side script such as JavaScript, jQuery, Angular etc.
 * License Key. License key authentication is best for situations where simplicity is required and you can keep the key private. An ideal use case for key authentication would be for server based apps calling our RESTful API.

Accessing the API using key authentication
------------------------------------------
Access the :abbr:`API(Application Programmers Interface)` at::

	https://api.emailverifyapi.com/api/a/v1?key=yourapikey&email=test@tester.com
	
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
| correct   | **1** (this will remove certain invalid characters)     | optional |
|           |                                                         |          |
|           | **0** (this will leave the email untouched)             |          |
+-----------+---------------------------------------------------------+----------+

Accessing the API using ACL authentication
------------------------------------------

::

	https://api.emailverifyapi.com/api/b/v1?email=test@tester.com

For ACL based authentication, it is not necessary to include the license key in the request. Other parameters (e.g. ‘correct’) are supported as in the key based example as in :ref:`figure1`.

Responses
---------
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

**Example response for email address ‘test@tester.com’**

The URL passed to the API is :-

::

	https://api.emailverifyapi.com/api/a/v1?key=yourapikey&email=test@tester.com

The response would be :-

::

	{
	"status":"Bad",
	"additionalStatus":"MailboxDoesNotExist",
	"emailAddressProvided":"test@tester.com",
	"emailAddressChecked":"test@tester.com",
	"emailAddressSuggestion":""
	}

The ‘correct’ Parameter
-----------------------
Optionally, you can also use the ‘correct’ parameter to remove certain invalid characters such as spaces, slashes, square brackets etc. Example using the ‘correct’ parameter. The user enters an email address john99]@gmail.com Here is the API call that would be made :-

::

	http://api.emailverifyapi.com/api/a/v1?key=yourapikey&email=john99]@gmail.com&correct=1

`emailverifyapi`_ will automatically remove the invalid character ‘]’ and send the corrected version through for validation. Example results based on the above API call :-

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
When an email address is returned with a status of ‘Bad’ or ‘Unknown’ we return the detailed reason as part of the response in the ‘additionalStatus’ value. For a full list of additional status values, please refer to the list `Detailed Response Codes`_.