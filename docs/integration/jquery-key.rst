jQuery (license key)
====================

.. code:: html

	<!DOCTYPE html>

	<!--
    *******************************************************************************************
    *   Company:
    *   (c) 2014, emailverifyapi.com (https://api.emailverifyapi.com)
    *
    *   File name:
    *   v1_key_acl.html
    *
    *   Version:
    *   1.0.20140827.0
    *
    *   Version control:
    *   - 1.0.20140827.0 - initial release
    *
    *   Date:
    *   August 2014
    *
    *   Description:
    *   Demonstrates how to call a RESTful service @ //api.emailverifyapi.com/api/a/v1
    *   using jQuery using client side only calls.
    *
    *   This example requires a valid key to work correctly.
    *
    *   License:
    *   Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0)
    *******************************************************************************************
    -->
	<html lang="en" xmlns="http://www.w3.org/1999/xhtml">
	<head>
		<meta charset="utf-8" />
		<title>emailverifyapi.com : License Key Sample.</title>
		<style type="text/css">
			.statusUnknown {
				color: #c1c72c;
			}

			.statusOk {
				color: #009933;
			}

			.statusBad, .errorMsg {
				color: #ff0000;
			}

			input[type='text'] {
				width: 300px;
			}
			p label {
				display: inline-block; width: 60px;
			}
		</style>
		<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
	</head>
	<body>
		<h1>emailverifyapi.com : email verification demo using simple key authentication with jQuery.</h1>
		<h2>About</h2>
		<p>This example shows how to perform email verification using just client side scripting and invoking a simple key based RESTful endpoint at <a href="https://api.emailverifyapi.com" target="_blank">api.emailverifyapi.com</a>.</p>
		<h2>How to run this sample</h2>
		<p>This page can be hosted anywhere (i.e. any web host or platform). The only thing needed is a valid license key.</p>
		<h2>Key features</h2>
		<ul>
			<li>Compatible with all modern browsers</li>
			<li>Uses jQuery 1.11.1</li>
			<li>No server side scripting required</li>
		</ul>
		<hr />
		<h2>Try it</h2>
		<p>
			<label for="key">Key:</label>
			<input type="text" id="key" name="key" tabindex="1" maxlength="20" />
		</p>
		<p>
			<label for="email">Email:</label>
			<input type="text" name="email" id="email" tabindex="2" />
			<input type="button" name="submit" id="submit" tabindex="3" value="verify" />
		</p>
		<div id="validationResult"></div> <!--Result output here-->
		<script>
				/*nest key logic inside document.ready to ensure functionality only available once document has fully loaded in browser.*/
				$(function () {
					console.log("ready!");

					$('#submit').click(function () {
						var emailText = $('#email').val(); // get key from text box entry
						var keyText = $('#key').val(); // get email address to be checked from text box

						if (keyText.length == 0) {
							$('#validationResult').html("<span class='errorMsg'>Please enter key.</span>");
							return;
						}

						if (emailText.length == 0) {
							$('#validationResult').html("<span class='errorMsg'>Please enter something for email.</span>");
							return;
						}
						
						$('#validationResult').html("verifying...");

						var emailVerifyApi = '//api.emailverifyapi.com/api/a/v1?email=' + encodeURIComponent(emailText) + '&key=' + keyText;

						/*execute remote request to perform email verification. Any errors will appear in the developer console (e.g. viewable using Chrome developer tools)*/
						$.getJSON(emailVerifyApi, {})
							.done(function (data) {
								reportResult(data);
							})
							.fail(function (jqxhr, textStatus, error) {
								var err = textStatus + ", " + error;
								console.log("Request failed: " + err);
							});;
					});
				});

				/*Output result to the 'validationResult' div element*/
				function reportResult(data) {
					var status = data['status'].toLowerCase(); // get 'status' from REST response
					var additionalStatus = data['additionalStatus']; // get 'additionalStatus' from REST response
					var message = data['Message']; // if there is an error (e.g. license issues), a notification will appear in the 'Message" from REST response.

					console.log(status);
					console.log(additionalStatus);
					console.log(message);

					var statusHtml;

					// if there is an error message, show here
					if (message != null
						&& message != '') {
						statusHtml = "<span class='errorMsg'>Error. Message='" + message + "' .</span>";
					} else {
						// map REST response data to presentation messages.
						switch (status) {
							case 'ok':
								statusHtml = "<span class='statusOk'>Email address is ok.</span>";
								break;
							case 'bad':
								statusHtml = "<span class='statusBad'>Email address is not valid.</span>";
								break;
							default:
								statusHtml = "<span class='statusUnknown'>Unable to validate email. Reason=" + additionalStatus + "</span>";
								break;
						}
					}

					console.log(statusHtml);

					// present the result on screen
					$('#validationResult').html(statusHtml);
				}
		</script>
	</body>
	</html>
	
