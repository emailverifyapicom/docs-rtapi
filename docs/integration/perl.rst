PERL
====

.. code:: perl

	###########################################################################################
    #   Company:
    #   (c) 2014, emailverifyapi.com (https://api.emailverifyapi.com)
    #
    #   File name:
    #   Program.pl
    #
    #   Version:
    #   1.0.20140828.0
    #
    #   Version control:
    #   - 1.0.20140828.0 - initial release
    #
    #   Date:
    #   August 2014
    #
    #   Description:
    #   Demonstrates how to call a RESTful service @ //api.emailverifyapi.com/api/a/v1
    #   using Perl using client side only calls.
    #
    #   This example requires a valid key to work correctly.
    #
    #   License:
    #   Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0)
    ###########################################################################################
	use LWP;

	# The url for the service
	$ApiUrl = "http://api.emailverifyapi.com/api/a/v1";

	# The format  of the full query string
	$QueryFormatString = "%s?email=%s&key=%s";

	print "Enter Email:\n";
	$readLine = <STDIN>;

	# The API key provided for your account goes here
	$YourAPIKey = "<!-- ENTER A VALID KEY HERE-->";

	# Format the url request
	$requestUrl = sprintf $QueryFormatString, $ApiUrl, $readLine, $YourAPIKey;

	# Make the request against the REST service
	$browser = LWP::UserAgent->new;
	$response = $browser->get($requestUrl);

	# Print the response
	print $response->content;