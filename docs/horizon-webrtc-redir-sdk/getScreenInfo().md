---
layout: page
title: getScreenInfo()
hide:
  #- navigation
  - toc
---

Gets information about the monitors connected to the client system.

### Parameters
None

### Return Values
| Type    | Description |
|---------|-------------|
| Promise | Resolves to an array of screen info objects or rejects with an error |

### Code Example
```js
let _screenInfo = await HorizonWebRtcRedirectionAPI.getScreenInfo();
```
