# Blazor-Links

2024-04-03 Cross platform, browser based Blazor progressive web application (PWA) for displaying html links with page navigation. Links are read from json file. Also supporting https://username:password@ links. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND (MIT)...


Repository contains both Blazor C# source code and binary together. You can test from [](https://jussivirkkala.github.io/Blazor-Links/)https://jussivirkkala.github.io/Blazor-Links/

# Cloning

If you are just cloning repository and not rebuilding binary (not recommended as you should never trust any binary files) then you need to modify only docs\index.html for correct location
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
    "type": 3,
    "label": "links e.g. blazor.net",
    "link": "https://www.blazor.net"
  },
  {
    "type": 4,
    "label": "links with https://username:password@www.something.com",
    "link": ""
  },
  {
    "type": 2,
    "label": "branch to data/page.json",
    "link": "page.json"
  }
]
```
There are different types of links: 1 labels supporting html, 2 branch links indicating \data\.json file, 3 standard links, and 4 username:password@ links. You can also modify .\index.html and \css for custon layout.

# Mobile

For iOS (tested iPadOS, iOS 16.6) and Anroid (tested Android 14) you can disable pull to refresh, text selection with following \css\app.css.
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

# Build, deploy

```
dotnet publish -c Release

Blazor-Links\bin\Release\net8.0\publish\wwwroot\
```
Remove .gz and .br files in _framework. For github pages add .nojekyll file

```
async function onInstall(event) {
    console.info('Service worker: Install');

    // Fetch and cache all matching items from the assets manifest
    const assetsRequests = self.assetsManifest.assets
        .filter(asset => offlineAssetsInclude.some(pattern => pattern.test(asset.url)))
        .filter(asset => !offlineAssetsExclude.some(pattern => pattern.test(asset.url)))
        .map(asset => new Request(asset.url, { integrity: asset.hash, cache: 'no-cache' }));
    await caches.open(cacheName).then(cache => cache.addAll(assetsRequests));
}
```
Remove integrity check

```
async function onInstall(event) {
    console.info('Service worker: Install');

    // Fetch and cache all matching items from the assets manifest
    const assetsRequests = self.assetsManifest.assets
        .filter(asset => offlineAssetsInclude.some(pattern => pattern.test(asset.url)))
        .filter(asset => !offlineAssetsExclude.some(pattern => pattern.test(asset.url)))
        .map(asset => new Request(asset.url));
    await caches.open(cacheName).then(cache => cache.addAll(assetsRequests));
}
```
Change index.

End
