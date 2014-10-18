VB.net
======

.. code-block:: vb.net

	Imports System.IO
	Imports System.Net
	 
	 
	''' <summary>
	''' The program.
	''' </summary>
	Friend Class Program
		#Region "Constants"
		 
		''' <summary>
		''' The api url.
		''' </summary>
		Private Const ApiUrl As String = "http://api.emailverifyapi.com/api/a/v1"
		 
		''' <summary>
		''' 0 = ApiUrl
		''' 1 = Email address to query
		''' 2 = API Key
		''' </summary>
		Private Const QueryFormatString As String = "{0}?email={1}&key={2}"
		 
		''' <summary>
		''' The your api key.
		''' </summary>
		''' <remarks>
		''' /*ENTER YOUR API KEY HERE*/
		''' </remarks>
		Private Const YourAPIKey As String = "<!-- ENTER A VALID KEY HERE-->"
		 
		#End Region
		 
		#Region "Methods"
		 
		''' <summary>
		''' The main program entry point.
		''' </summary>
		''' <param name="args">
		''' The args.
		''' </param>
		Private Shared Sub Main(args As String())
		
			Console.WriteLine("Input email address to verify")
			 
			Dim readLine = Console.ReadLine()
			 
			Console.WriteLine(String.Empty)
			 
			Dim requestUrl = String.Format(QueryFormatString, ApiUrl, readLine, YourAPIKey)
			 
			Dim myRequest = DirectCast(WebRequest.Create(requestUrl), HttpWebRequest)
			 
			Dim webResponse As WebResponse = Nothing
			 
			Try
				webResponse = myRequest.GetResponse()
				 
				Using reader = New StreamReader(webResponse.GetResponseStream())
					Dim jsonString = reader.ReadToEnd()
					 
					Console.ForegroundColor = ConsoleColor.Green
					Console.WriteLine("Result:")
					Console.WriteLine(jsonString)
					Console.ResetColor()
					Console.WriteLine("Press <Enter> to continue..")
					Console.ReadLine()
				End Using
			Catch exception As Exception
				Console.WriteLine("An error occured:")
				Console.ForegroundColor = ConsoleColor.Red
				Console.WriteLine("Exception reported: {0}", exception.Message)
				Console.ResetColor()
				Console.WriteLine("Press <Enter> to continue..")
				Console.ReadLine()
			Finally
				If webResponse IsNot Nothing Then
					webResponse.Dispose()
				End If
			End Try
		End Sub
		 
		#End Region
	End Class