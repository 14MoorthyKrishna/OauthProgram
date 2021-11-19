# OauthProgram
Microsoft.Owin.Security.OAuth
Microsoft.Owin.Cors
Microsoft.AspNet.WebApi.Core
Microsoft.AspNet.WebApi.Owin

public static async Task<string> GetAuthorizeToken()  
        {  
            // Initialization.  
            string responseObj = string.Empty;  
...  
            // Posting.  
            using (var client = new HttpClient())  
            {  
                // Setting Base address.  
                client.BaseAddress = new Uri("http://localhost:3097/");  
  
                // Setting content type.  
                client.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));  
...  
                // Initialization.  
                HttpResponseMessage response = new HttpResponseMessage();  
                List<KeyValuePair<string, string>> allIputParams = new List<KeyValuePair<string, string>>();  
  
                // Convert Request Params to Key Value Pair.  
...  
                // URL Request parameters.  
                HttpContent requestParams = new FormUrlEncodedContent(allIputParams);  
  
                // HTTP POST  
                response = await client.PostAsync("Token", requestParams).ConfigureAwait(false);  
  
                // Verification  
                if (response.IsSuccessStatusCode)  
                {  
                     // Reading Response.  
...  
                }  
            }  
  
            return responseObj;  
        }  
