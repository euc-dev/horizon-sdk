---
layout: page
title: initSDK(appLogger, appName, eventCallback, sdkConfig)
hide:
  #- navigation
  - toc
---

Initializes the SDK so the application can access API methods.

### Parameters

| Name           | Description |
|----------------|-------------|
| `appLogger`    | *(Optional)* An object with functions like `error`, `info`, and `warn` (compatible with `console`) |
| `appName`      | *(Required)* A string that names the application |
| `eventCallback`| *(Optional)* A callback function to receive events from the SDK |
| `sdkConfig`    | *(Optional)* A configuration object provided the following options.<br> `numOfCallConfigs`: The default value for the numOfCallConfigs is 1 if the numOfCallConfigs is undefined. After initSDK() called, use the getCallConfigs(index) to retrieve the corresponding callConfig object. The callConfig object can be passed to newPeerConnectionEx() and getUserMediaEx() in order to allow different audio headset used for different RTCPeerConnection object.  |

### Return Values
| Value | Description |
|-------|-------------|
| `true`  | Initialization successful; SDK APIs can be used |
| `false` | Initialization failed; app will fall back to standard Electron behavior |

### Code Example
```js
HorizonWebRtcRedirectionAPI.initSDK(myAppLogger, "My App Name", myCallbackFn);
```

```js
let sdkConfig = { numOfCallConfigs: 2 };
HorizonWebRtcRedirectionAPI.initSDK(myAppLogger, "My App Name", myCallbackFn, sdkConfig);
```