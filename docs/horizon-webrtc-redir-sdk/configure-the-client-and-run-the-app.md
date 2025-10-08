---
layout: page
title: Configure the Client and Run the App
hide:
  #- navigation
  - toc
---

### Configure electron client and run
1. Make sure you have NodeJS(latest stable version will be good enough) installed in your environment.
2. Copy client folder to wherever you want
3. Set the link url for index page in ‘client/serverInfo.json’. depends on how you configure your web server in steps above. Example: "pageUlr": "https://192.168.1.101/sample/index.html"
4. Set the Web Socket server ulr for ‘callServerUrl’ in ‘client/ serverInfo.json’, depends on how you configure your web socket server in steps above. Example: "callServerUrl": “wss://192.168.1.200:8443”
5. The final hierarchy should look like this
```
|--- client
   |--- main.js
   |--- preload.js
   |--- package.json
   |--- serverInfo.json
```   
6. Enter ./client folder, execute: 'npm install' and then 'npm start'

### Configure web client and run
1. Launch chrome browser and natigate to the url 
2. Add the Horizon WebRTC SDK browser extension to your chrome browser.
3. Note the IP address of your httpServer and the signaling server that will be used in step 4
4. Configure the following registry keys.
```
[HKLM\SOFTWARE\Policies\Omnissa\Horizon\WebRTCRedirSDKWebApp]
"enabled"=dword:00000001<br>
"chrome_enabled"=dword:00000001<br>
"edge_chrome_enabled"=dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Omnissa\Horizon\WebRTCRedirSDKWebApp\UrlAllowList]
"https://httpServerIpAddress:3000/*"=""
```
5. Close and reopen the VM then navigate to https://httpServerIpAddress:3000/webIndex.html?callServerUrl=wss://signalingServerIpAddress:8443

