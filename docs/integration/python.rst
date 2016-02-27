Python
======

.. code-block:: python

    ###########################################################################################
    #   Company:
    #   (c) 2016, emailhippo.com (https://www.emailhippo.com)
    #
    #   Version:
    #   1.0.20140827.0
    #
    #   Version control:
    #   - 1.0.20140827.0 - initial release
    #
    #   Date:
    #   August 2014
    #
    #   Description:
    #   Demonstrates how to call a RESTful service @ //api1.27hub.com/api/a/v1
    #   using Python
    #
    #   This example requires a valid key to work correctly.
    #
    #   License:
    #   Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0)
    ###########################################################################################

	# Import the module for handling the http request
	import urllib.request

	# The url for the service
	ApiUrl = "http://api1.27hub.com/api/a/v1"

	# The format  of the full query string
	QueryFormatString = "{0}?email={1}&key={2}"

	# The API key provided for your account goes here
	YourAPIKey = "<!-- ENTER A VALID KEY HERE-->"

	# Read in the user input
	readLine = input("Enter Email:\n")

	# Format the full url and make the http GET request and read the response
	response = urllib.request.urlopen(QueryFormatString.format(ApiUrl, readLine, YourAPIKey)).read()

	# Print the response
	print(response)
