# How to add Blazorise components in your MAUI Blazor Application

For more information about **Blazorise** components visit this URL: 

https://blazorise.com/docs/start

## 1. Run Visual Studio 2022 Community Edition and create a MAUI Blazor Application

We download Visual Studido 2022 Preview

https://visualstudio.microsoft.com/vs/preview/

![image](https://github.com/user-attachments/assets/08ba47c2-c95e-4f23-914e-05d174465deb)

We install .NET 9 SDK 

https://dotnet.microsoft.com/en-us/download/dotnet/9.0

![image](https://github.com/user-attachments/assets/1f73e7c8-1288-41f0-9e2d-60177818bd54)

We run Microsoft Visual Studio Community 2022 (64 bits) - Preview Versión 17.12.0 Preview 2.1

![image](https://github.com/user-attachments/assets/d7a4f524-fdb1-4f16-8c0f-52314ff8303d)

We create a new project

![image](https://github.com/user-attachments/assets/9334a2bb-9ed5-4c40-a312-26973910975f)

We search for MAUI projects templates and select .NET MAUI Blazor App

![image](https://github.com/user-attachments/assets/8287f785-96b9-417b-b457-bf34560320e8)

We input the project name and the location in the hard disk and we select the Framework .NET 9

This is the project folders and files structure

![image](https://github.com/user-attachments/assets/777c71ca-4d30-4969-855e-3414f91ef5c5)

## 2. Add the Blazorise Nuget package

Install a Bootstrap 5 provider for Blazorise:

```
Install-Package Blazorise.Bootstrap5
```

You also need to install the icon package:

```
Install-Package Blazorise.Icons.FontAwesome
```

![image](https://github.com/user-attachments/assets/8be580fe-0a1a-46fb-b4f5-a9d60df0a99e)

## 3. Modify the index.html file and add new code

These are the new lines to add in the index.html file

```
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">
<link href="_content/Blazorise/blazorise.css" rel="stylesheet" />
<link href="_content/Blazorise.Bootstrap5/blazorise.bootstrap5.css" rel="stylesheet" />
```

This is the modified index.html file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover" />
    <title>MAUIBlazorise</title>
    <base href="/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link rel="stylesheet" href="css/app.css" />
    <link rel="stylesheet" href="MAUIBlazorise.styles.css" />
    <link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">
    <link href="_content/Blazorise/blazorise.css" rel="stylesheet" />
    <link href="_content/Blazorise.Bootstrap5/blazorise.bootstrap5.css" rel="stylesheet" />
    <link rel="icon" href="data:,">
</head>

<body>

    <div class="status-bar-safe-area"></div>

    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>

    <script src="_framework/blazor.webview.js" autostart="false"></script>

</body>

</html>
```

## 4. Modify the _imports.razor file

We add this new line:

```
@using Blazorise
```

This is the modified _imports.razor code:

```razor
@using System.Net.Http
@using System.Net.Http.Json
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.AspNetCore.Components.Web.Virtualization
@using Microsoft.JSInterop
@using MAUIBlazorise
@using MAUIBlazorise.Components
@using Blazorise
```

## 5. Modify the middleware (MauiProgram.cs)

Please include the following code:

```csharp
using Blazorise;
using Blazorise.Bootstrap5;
using Blazorise.Icons.FontAwesome;

builder.Services
    .AddBlazorise( options =>
    {
        options.Immediate = true;
    } )
    .AddBootstrap5Providers()
    .AddFontAwesomeIcons();
```

This is the modified **MauiProgram.cs** file:

```csharp
using Blazorise;
using Blazorise.Bootstrap5;
using Blazorise.Icons.FontAwesome;
using Microsoft.Extensions.Logging;

namespace MAUIBlazorise
{
    public static class MauiProgram
    {
        public static MauiApp CreateMauiApp()
        {
            var builder = MauiApp.CreateBuilder();
            builder
                .UseMauiApp<App>()
                .ConfigureFonts(fonts =>
                {
                    fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
                });

            builder.Services.AddMauiBlazorWebView();
            builder.Services
                .AddBlazorise(options =>
                {
                    options.Immediate = true;
                })
                .AddBootstrap5Providers()
                .AddFontAwesomeIcons();

#if DEBUG
            builder.Services.AddBlazorWebViewDeveloperTools();
    		builder.Logging.AddDebug();
#endif

            return builder.Build();
        }
    }
}
```

## 6. Running the Blaozr MAUI application in your Mobile Device

Befor running your application in the Mobile you have to select the following menu option:

![image](https://github.com/user-attachments/assets/76ac1d98-06fd-49d1-8f68-d144fa102803)

Then you have to check the **Implement** option 

![image](https://github.com/user-attachments/assets/c7559339-ebc8-4d5f-a3bf-6a9e8a6da182)

Then connect your Mobile to your laptop with an USB wire and click on the run button:

![image](https://github.com/user-attachments/assets/f234b4f8-84fc-4806-8626-aa807aef7622)

![image](https://github.com/user-attachments/assets/5488a65d-30f8-442a-bf9b-a4bbfc56e2e3)

![image](https://github.com/user-attachments/assets/2043ee6e-18d1-47d5-9bcb-d524d1273e59)

![image](https://github.com/user-attachments/assets/e13994b7-6553-490e-ae4b-545c3dd1016e)

![image](https://github.com/user-attachments/assets/2b000193-3c41-401f-b3eb-d36efe61cb31)

![image](https://github.com/user-attachments/assets/96b65c37-c095-4771-baa3-3218e40856ad)

## 7. Running the Blazor MAUI application in Windows Desktop

![image](https://github.com/user-attachments/assets/2fd2d955-b8bf-4b51-bb7d-a77c1d343424)

![image](https://github.com/user-attachments/assets/db65b357-254e-4318-8cc9-ba3b36ae1d78)

![image](https://github.com/user-attachments/assets/e6c727ce-6eab-4d84-a8e2-2f9ac915cdf8)

![image](https://github.com/user-attachments/assets/9af54f61-50f0-4587-b8b7-a49c58d0e192)

