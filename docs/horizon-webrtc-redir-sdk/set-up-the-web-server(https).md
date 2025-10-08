---
layout: page
title: Set Up the Web Server (https)
hide:
  #- navigation
  - toc
---

1. Make sure you have NodeJS(latest stable version will be good enough) installed in your environment. For the httpServer you can also use any other statically hosting solution.
2. Copy the httpServer folder to the location you want to host.
3. Copy the folders 'sdk' into httpServer folder.
4. Gather a certificate, self signed is fine and place it into a folder called 'certs'. The final hierarchy should look like this:
```
|--- httpServer
   |--- httpServer.js
   |--- index.html
   |--- common
      |--- constant.js
   |--- sdk
      |--- HorizonSDKforWebRTCRedir.js
   |--- app
      |--- appMain.js
      |--- callMgr.js
      |--- ui.js
      |--- utils.js
|--- certs
   |--- cert.pem
   |--- key.pem
```
5. Enter the ./httpServer folder and run 'npm install' then 'npm start' (or node httpServer.js)
