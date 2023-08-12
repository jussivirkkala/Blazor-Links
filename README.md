# Blazor-Links

2023-08-12 Cross platform, browser based Blazor progressive web application (PWA) for displaying html links with page navigation. Links are read from json file. Also supporting https://username:password@ links. NOTICE THAT USERNAME AND PASSWORD IS STORED IN BROWSER LOCALSTORAGE. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND...

Repository contains both Blazor C# source code and binary together. I know it is not optimal. You can test from [](https://jussivirkkala.github.io/Blazor-Links/)https://jussivirkkala.github.io/Blazor-Links/

# Cloning

If you are just cloning repository and not rebuilding binary (not recommended as you should never trust any binary files) then you need to modify only \index.html for correct location
```
  <title>Blazor-Links</title>
    <base href="https://jussivirkkala.github.io/Blazor-Links/" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="manifest.json" rel="manifest" />
```
For custom links modify \data\.json files. Main.json is loaded by default. 
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
]
```
There are different types of links: 0 branch links indicating \data\.json file, 1 labels supporting html, 2 standard links, and 3 username:password@ links. You can also modify .\index.html and \css for custon layout.

# Mobile

For iOS (tested iPadOS 16.6) and Anroid (tested Android 14) you can disable pull to refresh, text selection with following \css\app.css.
```
html {
    overscroll-behavior : none;
    -webkit-user-select: none; /* Safari */
    -ms-user-select: none; /* IE 10 and IE 11 */
    user-select: none; /* Standard syntax */
}
body {
    overflow-y: scroll;
    overscroll-behavior : contain;
}
html {
overscroll-behavior : none;
}
```
To disable mobile pinch to zoom in or out \index.html contains following lines
```
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, minimum-scale=1, height=device-height, viewport-fit=cover" />
    <meta name="mobile-web-app-capable" content="yes" />
    <meta name="apple-mobile-web-app-capable" content="yes" />
```

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
