C#
==

.. code-block:: c#

	#region Usings
 
	using System;
	using System.IO;
	using System.Net;
	 
	#endregion
	 
	/// <summary>
	/// The program.
	/// </summary>
	internal class Program
	{
		#region Constants
		 
		/// <summary>
		/// The api url.
		/// </summary>
		private const string ApiUrl = @"http://api.emailverifyapi.com/api/a/v1";
		/// <summary>
		/// 0 = ApiUrl
		/// 1 = Email address to query
		/// 2 = API Key
		/// </summary>
		private const string QueryFormatString = @"{0}?email={1}&key={2}";
		 
		/// <summary>
		/// The your api key.
		/// </summary>
		/// <remarks>
		/// /*ENTER YOUR API KEY HERE*/
		/// </remarks>
		private const string YourAPIKey = @"<!-- ENTER A VALID KEY HERE-->";
		 
		#endregion
		 
		#region Methods
		 
		/// <summary>
		/// The main program entry point.
		/// </summary>
		/// <param name="args">
		/// The args.
		/// </param>
		private static void Main(string[] args)
		{
			Console.WriteLine("Input email address to verify");
			 
			var readLine = Console.ReadLine();
			 
			Console.WriteLine(string.Empty);
			 
			var requestUrl = string.Format(QueryFormatString, ApiUrl, readLine, YourAPIKey);
			 
			var myRequest = (HttpWebRequest)WebRequest.Create(requestUrl);
			 
			WebResponse webResponse = null;
			 
			try
			{
				webResponse = myRequest.GetResponse();
				 
				using (var reader = new StreamReader(webResponse.GetResponseStream()))
				{
					var jsonString = reader.ReadToEnd();
					 
					Console.ForegroundColor = ConsoleColor.Green;
					Console.WriteLine("Result:");
					Console.WriteLine(jsonString);
					Console.ResetColor();
					Console.WriteLine("Press <Enter> to continue..");
					Console.ReadLine();
				}
			}
			catch (Exception exception)
			{
				Console.WriteLine("An error occured:");
				Console.ForegroundColor = ConsoleColor.Red;
				Console.WriteLine("Exception reported: {0}", exception.Message);
				Console.ResetColor();
				Console.WriteLine("Press <Enter> to continue..");
				Console.ReadLine();
			}
			finally
			{
				if (webResponse != null)
				{
					webResponse.Dispose();
				}
			}
		}
		 
		#endregion
	}