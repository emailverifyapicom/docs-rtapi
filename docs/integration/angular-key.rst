AngularJS (license key)
=======================

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
    *   using AngularJS with client side only calls.
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
			input[type='text'],input[type='email'] {
				width: 300px;
			}
			p label {
				display: inline-block;
				width: 60px;
			}
		</style>

	</head>
	<body>
		
		<h1>emailverifyapi.com : email verification demo using simple key authentication with AngularJS.</h1>
		<h2>About</h2>
		<p>This example shows how to perform email verification using just client side scripting and invoking a simple key based RESTful endpoint at <a href="https://api.emailverifyapi.com" target="_blank">api.emailverifyapi.com</a>.</p>
		<h2>How to run this sample</h2>
		<p>This page can be hosted anywhere (i.e. any web host or platform). The only thing needed is a valid license key.</p>
		<h2>Key features</h2>
		<ul>
			<li>Compatible with all modern browsers</li>
			<li>Uses AngularJS 1.2.23</li>
			<li>No server side scripting required</li>
		</ul>
		<hr />
		<h2>Try it</h2>
		<div id="MyApp" ng-app="apiDemo" ng-controller="apiDemoController">
			<form name="verifyForm" novalidate="" ng-submit="doVerify()">
				<p>
					<label for="key">Key:</label>
					<input type="text" id="key" name="key" tabindex="1" maxlength="20" ng-model="query.key" required="" />
					<span class="errorMsg" ng-show="verifyForm.key.$error.required">*</span>
				</p>
				<p>
					<label for="email">Email:</label>
					<input type="email" name="email" id="email" tabindex="2" ng-model="query.email" required="" />
					<span class="errorMsg" ng-show="verifyForm.email.$error.required">*</span>
					<span class="errorMsg" ng-show="verifyForm.email.$error.email">not valid email</span>
				</p>
				<p>
					<label>&nbsp;</label>
					<input type="submit" name="submit" id="submit" tabindex="3" value="verify" />
				</p>
			</form>
			<div id="validationResult"><!--Result output here-->
				<div ng-show="showValidating">verifying..</div>
				<div ng-show="showOk"><span class="statusOk">Email address is ok.</span></div>
				<div ng-show="showBad"><span class="statusBad">Email address is not valid.</span></div>
				<div ng-show="showUnknown"><span class="statusUnknown">Unable to validate email. Reason={{additionalStatusMessage}}</span></div>
				<div ng-show="showMessage"><span class="errorMsg">Error. Message={{errorMessage}}</span></div>
			</div>
		</div>

		<script src="//ajax.googleapis.com/ajax/libs/angularjs/1.2.23/angular.min.js"></script>
		
		<script>

			// Module
			var app = angular.module('apiDemo', []);

			// Controller
			app.controller('apiDemoController', function apiDemoController($scope,$http) {
				$scope.query = {
					key: "",
					email: ""
				};

				$scope.result = {
					status: "",
					additionalStatus: ""
				};

				// verification event
				$scope.doVerify = function () {
					resetMessage();
					$scope.showValidating = true;
					var emailVerifyApi = '//api.emailverifyapi.com/api/a/v1?email=' + encodeURIComponent($scope.query.email) + '&key=' + $scope.query.key;
					console.log(emailVerifyApi);
					$http.get(emailVerifyApi)
						.success(function (response) {
							resetMessage();
							var status = response['status'].toLowerCase();
							var additionalStatus = response['additionalStatus'];
							var message = response['Message'];

							console.log(status);
							console.log(additionalStatus);
							console.log(message);
							
							// if there is an error message, show here
							if (message != null
								&& message != '') {
								$scope.errorMessage = message;
								$scope.showMessage = true;

							} else {
								// map REST response data to presentation messages.
								switch (status) {
									case 'ok':
										$scope.showOk = true;
										break;
									case 'bad':
										$scope.showBad = true;
										break;
									default:
										$scope.additionalStatusMessage = additionalStatus;
										$scope.showUnknown = true;
										
										break;
								}
							}
					});

					// 
					function resetMessage() {
						$scope.showValidating = false;
						$scope.showBad = false;
						$scope.showMessage = false;
						$scope.showOk = false;
						$scope.showUnknown = false;
						$scope.showMessage = false;
					}
				}
			});

			
		</script>

	</body>
	</html>
	
