# OauthProgram
Microsoft.Owin.Security.OAuth
Microsoft.Owin.Cors
Microsoft.AspNet.WebApi.Core
Microsoft.AspNet.WebApi.Owin

namespace Books.ListMyLibrary
{
    internal class Program
    {
        static void Main(string[] args)
        {
            try
            {
                new Program().Run().Wait();
            }
            catch (AggregateException ex)
            {
                foreach (var e in ex.InnerExceptions)
                {
                    Console.WriteLine("ERROR: " + e.Message);
                }
            }
        }
        private async Task Run()
        {
            UserCredential credential;
            using (var stream = new FileStream("client_secrets.json", FileMode.Open, FileAccess.Read))
            {
                credential = await GoogleWebAuthorizationBroker.AuthorizeAsync(
                    GoogleClientSecrets.Load(stream).Secrets,
                    new[] { BooksService.Scope.Books },
                    "user", CancellationToken.None, new FileDataStore("Books.ListMyLibrary"));
            }
            var service = new BooksService(new BaseClientService.Initializer()
                {
                    HttpClientInitializer = credential,
                    ApplicationName = "Books API Sample",
                });
            var bookshelves = await service.Mylibrary.Bookshelves.List().ExecuteAsync();
        }
    }
}
  
