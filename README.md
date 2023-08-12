# Blazor-Links

2023-08-12 Cross platform, browser based Blazor progressive web application (PWA) for displaying html links with page navigation. Links are read from json file. Also supporting https://username:password@ links. ISERNAME AND PASSWORD IS STORED IN LOCALSTORAGE

This repository contains both Blazor C# source code and binary together (I know it is not optimal). You can test from from [](https://jussivirkkala.github.io/Blazor-Links/)https://jussivirkkala.github.io/Blazor-Links/

# Cloning

If you are just cloning repository and not rebuilding binary (not recommended as you should never trust any binary files) then you do not need to modify only modify \index.html for correct location
```
  <title>Blazor-Links</title>
    <base href="https://jussivirkkala.github.io/Blazor-Links/" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="manifest.json" rel="manifest" />
```
For custom links modify \data\.json files. Main.json is loaded by default
```
[
  {
    "type": 1,
    "label": "<b>See data/main.json v1.0.5</b>",
    "link": ""
  },
  {
    "type": 2,
    "label": "links e.g. blazor.net",
    "link": "https://www.blazor.net"
  },
  {
    "type": 3,
    "label": "links with https://username:password@www.something.com",
    "link": ""
  },
  {
    "type": 0,
    "label": "branch to data/page.json",
    "link": "page.json"
  }
]```
There are different types of links: 0 branch links indicating \data\.json file, 1 labels supporting html, 2 standard links, and 3 username:password@ links

# Mobile


With iOS (tested iPadOS 16.6) you can disable pull to refresh with following css.
```
html {
overscroll-behavior : none;
}

body {
overflow-y: scroll;
}
```

With Android (tested Android 13)
```
html {
overscroll-behavior : none;
}

body {
overscroll-behavior : contain;
}
```
To disble pinch to zoom in or out

```
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, minimum-scale=1, height=device-height, viewport-fit=cover" />
    <meta name="mobile-web-app-capable" content="yes" />
    <meta name="apple-mobile-web-app-capable" content="yes" />
```



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
