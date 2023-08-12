# Blazor-Links

2023-08-05 Cross platform, browser based Blazor progressive web application (PWA) for displaying html links with page navigation. Also supportin https://username:password@ links. PASSWORD IS STORED IN LOCALSTORAGE

This repository contains both Blazor C# source code and binary together. . You can test the from [](https://jussivirkkala.github.io/Blazor-Links/)https://jussivirkkala.github.io/Blazor-Links/

# Cloning

If you are just cloning repository and not rebuilding binary (not recommended as you should not trust any binary files) then you do not need to modify \wwwroot folder but just once index.html for correct location
```
  <title>Blazor-Links</title>
    <base href="https://jussivirkkala.github.io/Blazor-Links/" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="manifest.json" rel="manifest" />
```

# Mobile
```
html {
overscroll-behavior : none;
}
```

With iOS
```

body {
overflow-y: scroll;
}
```
With Android
body {
overflow-y: scroll;
overscroll-behavior : contain;
}



data folder .json files for custom content and css folder custom look. 


If you clone repository and want to modify links you can modify also \data \css folders

| App folder| Content|
| -------- | ------- |
| _framework| 
| index.html | , deployment uses formdata\index.html files|
| css| css files, deployment uses formdata folder |
| data| .json files for links, deployment uses formdata folder | 



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
