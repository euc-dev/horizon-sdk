---
layout: page
title: getWindowHandleForWebApp()
hide:
  #- navigation
  - toc
---

Returns the **window handle (hwnd)** for the current browser tab.

This function is useful in environments where your application runs inside a browser and needs to retrieve the associated window handle for SDK operations.

> **Note:** The tab must be **unique**. Use `onTitleChanged()` to ensure the correct title is being tracked.

### Parameters
None

### Return Values
| Type    | Description |
|---------|-------------|
| Promise | Resolves with the `hwnd` (window handle) once retrieved from the server |

### Code Example
```js
let hwnd = await VMwareWebRtcRedirectionAPI.getWindowHandleForWebApp();
```
