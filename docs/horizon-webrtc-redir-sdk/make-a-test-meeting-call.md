---
layout: page
title: Configure Client and Run App
hide:
  #- navigation
  - toc
---

This section describes the steps to run the sample app included with the SDK.

> **Note:** Alternatively, you can build your own client app on the Electron framework, as described in the [Electron Quick Start Guide](https://www.electronjs.org/docs/latest/tutorial/quick-start#package-and-distribute-your-application).

## Steps to Run the App from the Client Machine

1. Ensure that you have NodeJS installed in your environment. It’s recommended that you install the latest stable version of NodeJS.
2. In `./client/serverInfo.json`, configure the index page URL for `pageUrl`. For example:
    ```json
    "pageUrl": "https://192.168.1.101/sample/index.html"
    ```
    In the example, `192.168.1.101` is the Web server address, and `sample` is the web application folder on the Web server where you copied the `index.html` file and the `sdk`, `common`, and `app` folders. Replace these example values with your own information.
3. In `./client/serverInfo.json`, configure the value of `callServerUrl`. For example:
    ```json
    "callServerUrl": "wss://192.168.1.200:8443"
    ```
    In the example, `192.168.1.200` is the Web Socket server address, and `8443` is the port number configured in `./server/wsServer.js`. Replace these example values with your own information.
4. To start the app, change to the `./client` directory and run `npm start`.
