Java
====
.. code-block:: java

	/*
	*******************************************************************************************
	* Company:
	* (c) 2016, email-checker.com (https://www.emailhippo.com)
	*
	* File name:
	* java.v1_key_acl
	*
	* Version:
	* 1.0.20140827.0
	*
	* Version control:
	* - 1.0.20140827.0 - initial release
	*
	* Date:
	* August 2014
	*
	* Description:
	* Demonstrates how to call a RESTful service @ //api1.27hub.com/api/a/v1
	* using java.
	*
	* This example requires a valid key to work correctly.
	*
	* License:
	* Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0)
	*******************************************************************************************
	*/

	import java.io.BufferedReader;
	import java.io.IOException;
	import java.io.InputStreamReader;
	import java.net.HttpURLConnection;
	import java.net.URL;
	import java.util.Scanner;
	import java.util.logging.Level;
	import java.util.logging.Logger;

	public class Program 
	{

		/*
		 * The URL which should be requested
		 */
		private static final String ApiUrl = "http://api1.27hub.com/api/a/v1";
		
		/*
		 * Query string for request
		 * %1$s = ApiUrl
		 * %2$s = Email address to query
		 * %3$s = API Key
		 */
		private static final String QueryFormatString = "%1$s?email=%2$s&key=%3$s";
		
		/*
		 * Your API Key
		 * 
		 */
		private static final String YourAPIKey = "/* ENTER A VALID KEY HERE */";
		
		/**
		 * The main program entry point
		 * @param args the command line arguments
		 * @throws IOException If the server does not return a success response
		 */
		public static void main(String[] args) 
		{
			System.out.println("Input email address to verify");
			
			// Create a scanner to read in the requested email address
			Scanner in = new Scanner(System.in);
			String readLine = in.next();
			  
			try 
			{
				// Format the request url to the correct structure for the request
				URL requestUrl = new URL(String.format(QueryFormatString, ApiUrl, readLine, YourAPIKey));
				
				// Open a connection to the website
				HttpURLConnection myRequest =  (HttpURLConnection) requestUrl.openConnection();
				
				// Set the type to HTTP GET
				myRequest.setRequestMethod("GET");

				// Create a new buffered reader to read the response back from the server
				BufferedReader reader = new BufferedReader(
					new InputStreamReader(myRequest.getInputStream()));
				
				String inputLine;
				StringBuilder response = new StringBuilder();
				
				// Read in the response line from the server
				while ((inputLine = reader.readLine()) !=null )
				{
					response.append(inputLine);
				}
				
				// Close the reader
				reader.close();
				
				// Output the result to console
				System.out.println(response.toString());
			} 
			catch (IOException ex) 
			{
				Logger.getLogger(Program.class.getName()).log(Level.SEVERE, null, ex);
			}
		}
		
	}

