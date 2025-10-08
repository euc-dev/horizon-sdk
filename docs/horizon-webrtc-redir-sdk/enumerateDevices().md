---
layout: page
title: enumerateDevices()
hide:
  #- navigation
  - toc
---

Gets the media device list and returns it to the application.  
This function is similar to [`MediaDevices.enumerateDevices()`](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/enumerateDevices).

### Parameters
None

### Return Values
| Type    | Description |
|---------|-------------|
| Promise | Resolves to an array of `MediaDeviceInfo` objects or rejects with a related `DOMException` |

### Code Example
```js
let _deviceList = await HorizonWebRtcRedirectionAPI.enumerateDevices();
```


