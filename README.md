
# Two Factor Authentication .NET
I needed to create a POC (Proof of Concept) of how to implement Two Factor Authentication, because we're create a new project that it will need use it. 

Below I'm going to show how to implementing two factor authentication with .net. 

## Autores

- [@ThiagoAntonioFerreira](https://github.com/ThiagoAntonioFerreira)

First I'll create a new project in Visual Studio.

![image](https://user-images.githubusercontent.com/2035948/222460693-91f0fea1-6a5a-4308-b76c-ce9c7b752fba.png)

In my project I'll install the packages to connect to SqlServer. 

Go to Tools -> Nuget Package Manager -> Package Manager Console and type this:

```bash
  dotnet add package Microsoft.EntityFrameworkCore --version 7.0.3
  
  dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore --version 7.0.3
```

After I install the packages in my Program.cs I configure my DbContext and Identity.

```c#
builder.Services.AddDbContext<ApplicationDbContext>(options => 
        options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));
        
builder.Services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = false)
    .AddEntityFrameworkStores<ApplicationDbContext>();
```

![image](https://user-images.githubusercontent.com/2035948/223128715-f9f6e972-96fd-4c03-82b3-47a1b623f198.png)

![image](https://user-images.githubusercontent.com/2035948/223128800-b006d4df-23e5-4a53-9ffc-219aea037b63.png)

![image](https://user-images.githubusercontent.com/2035948/223128869-e84e6162-c4ef-46fd-af7a-1f59ff54ae24.png)

![image](https://user-images.githubusercontent.com/2035948/223128964-844c5892-0db5-4217-a203-0fb056f2822d.png)

In my test I used another fictional email. After you login, you'll receive another screen where you have to type your code. I'm using Microsoft Authenticado, but you can user Google Authenticator as well.

![image](https://user-images.githubusercontent.com/2035948/223419728-b691be77-b539-4df2-8b27-d004754654bd.png)

