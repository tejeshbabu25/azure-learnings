# AppSettings.json file
- appsettings.json file could be used to store App keys in dot net core
- Using Microsoft.Extensions.Configuration namespace we have retrive the values from appsettings.json file 
-    for example var mykeyValue = Configuration["MyKey"];
- this file could become pretty long
- However , this is not the most secure way of doing this as once checked in it is saved forever in version control history

# So , Azure provides a couple of alternatives to store secrets


# Option one - On Azure Portal
    - App service - > Configuration - Application Settings

# Option two - Azure key vault
    - Specifically designed to keep secrets
    - Once a key vault app is created , we can use secrets to create new secrets
    - to work with from ASP.NET core application we can add references to below packages
            Azure.Extensions.AspNetCore.Configuration.Secrets
            Azure.Identity
    - To Access the keyVault from application we add below values to the appSettings.json file instead of actual key/values pairs

               {
                    "KeyVaultName": "Key Vault Name",
                    "AzureADApplicationId": "Azure AD Application ID",
                    "AzureADCertThumbprint": "Azure AD Certificate Thumbprint",
                    "AzureADDirectoryId": "Azure AD Directory ID"
               }

    - Then in the program.cs file , we can import below namespaces and do some cryptography and load of certificate we require like below

                using System.Security.Cryptography.X509Certificates;
                using Azure.Identity;

                var builder = WebApplication.CreateBuilder(args);

                if (builder.Environment.IsProduction())
                {
                    using var x509Store = new X509Store(StoreLocation.CurrentUser);

                    x509Store.Open(OpenFlags.ReadOnly);

                    var x509Certificate = x509Store.Certificates
                        .Find(
                            X509FindType.FindByThumbprint,
                            builder.Configuration["AzureADCertThumbprint"],
                            validOnly: false)
                        .OfType<X509Certificate2>()
                        .Single();

                    builder.Configuration.AddAzureKeyVault(
                        new Uri($"https://{builder.Configuration["KeyVaultName"]}.vault.azure.net/"),
                        new ClientCertificateCredential(
                            builder.Configuration["AzureADDirectoryId"],
                            builder.Configuration["AzureADApplicationId"],
                            x509Certificate));
                }

                var app = builder.Build();


 Cons
 - complicated
 - provide access to these secrets to users/applications
