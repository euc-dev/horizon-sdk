---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# `isFeatureSupported(feature)`

Checks whether the specified feature is supported by the SDK.

**Currently supported features:**
- `"video"`
- `"screenshare"`
- `"multimonitorscreenshare"`
- `"datachannel"`

### Parameters

| Name     | Description |
|----------|-------------|
| `feature` | *(Required)* Name of the feature to check |

### Return Values
| Value | Description |
|-------|-------------|
| `true`  | The feature is supported |
| `false` | The feature is not supported |

### Code Example
```js
let _isSupported = HorizonWebRtcRedirectionAPI.isFeatureSupported("datachannel");
```

