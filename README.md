# Blazor-Links

2023-08-05 Cross platform, browser based, Blazor progressive web application (PWA) for displaying html links

# Code
This repository contains both C# source code and binary. You can test the[ app at ](https://jussivirkkala.github.io/Blazor-Links/)https://jussivirkkala.github.io/Blazor-Links/

| App folder| Content|
| -------- | ------- |
| _framework| 
| index.html | , deployment uses formdata\index.html files|
| css| css files, deployment uses formdata folder |
| data| .json files for links, deployment uses formdata folder | 


# Cloning

If you are just cloning repository and not rebuilding binary (not recommended, you should not trust any binary files) then you do not need to modify wwwroot folder but just once index.html, data folder .json files for custom content and css folder custom look. 


# Deploy

After you deploy using Visual Studio 2022 or dotnet in command line folder Blazor-Links\bin\Release\net7.0\browser-wasm\publish\wwwroot contains

dotnet publish -c Release

Blazor-Links\bin\Release\net7.0\publish\

| Publish folder| Content|
| -------- | ------- |
| _framework | binary files |
| data |.json  |
| index.html |.json  |

Before copying these files

Modify in correct folder e.g. <base href="/blazor/edf/" /> in publish\wwwroot\index.html.

dotnet publish -c Release
