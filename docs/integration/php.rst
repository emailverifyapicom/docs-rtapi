PHP
===
.. code-block:: php
	
	<?php
 
	// URL which should be requested
	$url = 'http://api1.27hub.com/api/a/v1';
	 
	$apikey = 'YOUR API KEY'; // API Key
	 
	$email = 'Email Address to Test'; // Email to test
	 
	// jSON String for request
	$url .= "?email=$email&key=$apikey";
	 
	// Initializing curl
	$ch = curl_init( $url );
	 
	if($ch == false) {
	 
	die ("Curl failed!");
	 
	} else {
	 
	// Configuring curl options
	$options = array(
	CURLOPT_RETURNTRANSFER => true,
	CURLOPT_HTTPHEADER => array('Content-type: application/json')
	);
	 
	// Setting curl options
	curl_setopt_array( $ch, $options );
	 
	// Getting results
	$result = curl_exec($ch); // Getting jSON result string
	 
	// display JSON data
	echo "$result";
	 
	}
	 
	?>
	
