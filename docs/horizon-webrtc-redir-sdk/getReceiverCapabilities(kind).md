---
layout: page
title: getReceiverCapabilities(kind)
hide:
  #- navigation
  - toc
---

Acquires the `RTCRtpReceiver` capabilities on the client side.  
This function is similar to [`RTCRtpReceiver.getCapabilities()`](https://developer.mozilla.org/en-US/docs/Web/API/RTCRtpReceiver/getCapabilities).

### Parameters

| Name  | Description |
|-------|-------------|
| `kind` | *(Required)* The type of capabilities to acquire. Allowed values: `"audio"` or `"video"` |

### Return Values
| Type              | Description |
|-------------------|-------------|
| `RTCRtpCapabilities` | The capabilities object. [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/API/RTCRtpReceiver/getCapabilities#return_value) |

### Code Example
```js
let _caps = HorizonWebRtcRedirectionAPI.getReceiverCapabilities("video");
```


