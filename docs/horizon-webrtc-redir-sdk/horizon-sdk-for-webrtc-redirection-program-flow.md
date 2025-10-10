---
layout: page
title: Horizon SDK for WebRTC Redirection Program Flow
hide:
  #- navigation
  - toc
---

A typical Horizon WebRTC Redirection program flow involves two phases:
1. Initialization of the Application
2. Initialization of the Horizon SDK for WebRTC Redirection

## Application Initialization

The desktop-side Application startup is initiated by the user.

On launch, the Application:
- Calls the system API to get the current Windows session ID.
- Looks up these registry values:

| Registry Key | Description |
|--------------|-------------|
| `HKCU\Software\Omnissa\HTML5 Redirection Server\$(session id)\secureWebport` | Local Horizon Agent Web Socket port |
| `HKCU\Volatile Environment\$(session id)\ViewClient_Client_ID` | Horizon View client ID |

> These values are used by the Application to help initialize the SDK.

## SDK Initialization

The Application initializes the Horizon SDK by implementing three asynchronous functions under the `window` namespace:

| Function | Description |
|----------|-------------|
| `getHorizonClientID()` | Returns a Promise resolving to the Horizon View client ID. |
| `getHorizonWSSPort()` | Returns a Promise resolving to the WebSocket port. |
| `getWindowReference()` | Returns a Promise resolving to the current app window handle as a hex string. |

**Example: Calling an async function**

```javascript
let port = await window.getHorizonWSSPort();
```

You may optionally configure your app to provide a log object to the SDK during initialization. If no log is provided or if it's invalid, the SDK will fall back to using its built-in logging, viewable in the browser console.

> A valid logger should include methods like `error`, `info`, and `warn`, similar to the standard `console` object.
