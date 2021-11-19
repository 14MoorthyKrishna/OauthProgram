# OauthProgram
Microsoft.Owin.Security.OAuth
Microsoft.Owin.Cors
Microsoft.AspNet.WebApi.Core
Microsoft.AspNet.WebApi.Owin

public static async Task<string> GetAuthorizeToken()  
{  
        string responseObj = string.Empty;  
        using (var client = new HttpClient())  
        {  
                client.BaseAddress = new Uri("http://localhost:3097/");  
                client.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));  
                HttpResponseMessage response = new HttpResponseMessage();  
                List<KeyValuePair<string, string>> allIputParams = new List<KeyValuePair<string, string>>();  
                HttpContent requestParams = new FormUrlEncodedContent(allIputParams);  
                response = await client.PostAsync("Token", requestParams).ConfigureAwait(false);  
                if (response.IsSuccessStatusCode)  
                {  
                }  
            }  
            return responseObj;  
        }  
