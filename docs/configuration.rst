Configuration
=============

Authentication
--------------
Each call to the API must be authenticated. Authentication with the API is performed by either:

 * :abbr:`ACL(Access Control List)`. ACL is checked against the domain calling the API. ACL authentication does not require a license key and is best in situations where the API is being called from client side script such as JavaScript, jQuery, Angular etc.
 * License Key. License key authentication is best for situations where simplicity is required and you can keep the key private. An ideal use case for key authentication would be for server based apps calling our RESTful API.

Accessing the API using key authentication
------------------------------------------
Access the :abbr:`API(Application Programmers Interface)` at::

	https://api.emailverifyapi.com/api/a/v1
	
Sending the following parameters :-

+-----------+-----------------------------------------------------+----------+
| Parameter | Value                                               |          |
+===========+=====================================================+==========+
| key       | your unique API key supplied by us                  | required |
+-----------+-----------------------------------------------------+----------+
| email     | the email address to be validated                   | required |
+-----------+-----------------------------------------------------+----------+
| correct   | 1 (this will remove certain invalid characters)     | optional |
|           | 0 (this will leave the email untouched)             |          |
+-----------+-----------------------------------------------------+----------+
