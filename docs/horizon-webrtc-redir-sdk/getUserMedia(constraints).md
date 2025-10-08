---
layout: page
title: getUserMedia(constraints)
hide:
  #- navigation
  - toc
---

Retrieves the media stream from the local media device and returns it to the application.  
This function is similar to [`MediaDevices.getUserMedia()`](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia).

### Parameters

| Name        | Description |
|-------------|-------------|
| `constraints` | *(Required)* An object specifying the details of the media stream. [More info](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia#parameters) |

### Return Values
| Type    | Description |
|---------|-------------|
| Promise | Resolves to a `MediaStream` or rejects with a related `DOMException` |

### Code Example
```js
let _stream = await HorizonWebRtcRedirectionAPI.getUserMedia(_constraints);
```


