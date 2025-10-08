---
layout: page
title: Set Up the Signaling Server
hide:
  #- navigation
  - toc
---

You can set up the web server (https) and signaling server on either the same machine or on different machines. The servers can either share the same certificate-and-key pair or use different ones.
1. Make sure you have NodeJS(latest stable version will be good enough) installed in your environment.
2. Copy the 'sigServer' to the location you want to start.
3. Gather a certificate, self signed is fine and place it into a folder called 'certs'. copy the certs folder next to the sigServer
4. The final hierarchy should look like this:
```
|--- sigServer
   |--- wsServer.js
   |--- user.js
   |--- package.json
   |--- common
      |--- constant.js
|--- certs
   |--- cert.pem
   |--- key.pem
```   
5. Enter ./sigServer folder, execute: 'npm install' and then 'npm start' (or node wsServer.js)

