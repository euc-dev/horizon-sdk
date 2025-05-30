---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# Data Types and Error Codes

The Horizon Session Enhancement API has three groups of data types. The API also specifies error codes for various error conditions. 

## Data Types

The Horizon Session Enhancement API uses the following data types:

- VDP Service
- VDP RPC
- Overlay

### VDP Service Data Types

| Data Type | Description |
| --------- | ----------- |
| VDPService_ConnectionState | This enum indicates the current state of the remote connection. |
| VDPService_ChannelState | This enum indicates the current state of a particular channel. |
| VDPService_SessionType | This enum indicates the type of the current session (Blast Extreme or PCoIP). |

### VDP RPC Data Types

The VDP RPC data types are for use with the VDP RPC API.

| Data Type | Description |
| --------- | ----------- |
| VDP_RPC_VARENUM | This enum indicates the type of data that is stored in a VDP_RPC_VARIANT. |
| VDP_RPC_BLOB | Stores data that does not fit in any predefined VDP_RPC_VARENUM. Because VDP Service sends the data as is, it cannot protect against changes in byte endianness or structure alignment and padding. Use care to avoid errors. |
| VDP_RPC_VARIANT | Wraps the data for the RPC calls. Any data that is sent with the Invoke call must be contained in a VDP_RPC_VARIANT. |
| VDPRPC_ObjectState | Represents the state of an object. Only objects in the VDP_RPC_OBJ_CONNECTED state can be used in the `Invoke` call. |
| VDPRPC_ObjectConfigurationFlags | Used to configure channel objects with `ChannelObjectInterface.v1.CreateChannelObject`. |
| VDPRPC_ChannelContextOps | Used to configure the channel contexts with `ChannelContextInterface.v2.SetOps`. |
| VDPRPC_SideChannelType | Virtual side channel or TCP side channel. |

## VDPOverlay Data Types

The VDPOverlay data types are for use with the Overlay API. They are found in `vdpOverlay.h`.
This first table provides the VDP Overlay Guest data types. The second table provides the VDP Overlay Client data types.

### VDPOverlayGuest Data Types

| **Data Type**     | **Description**  |
| --------- | ----------- |
| VDPOverlay_WindowId             | An identifier that represents a remote or guest-side overlay. In earlier versions of the API, the `windowId` and the `HWND` were the same, but in the current version, they can be different.                                                                                           |
| VDPOverlay_HWND                 | A representation of the native OS window.                                                                                                                      |
| VDPOverlay_UserArgs             | Parameter that is passed through to the callback on the remote side.                                                                                           |
| VDPOverlay_LayoutMode           | This enum represents all of the different layouts that the VDP Overlay API supports.                      |
| VDPOverlay_Error                | Returned by many of the Overlay functions. Indicates the results that may occur.                                                      |
| VDP_OVERLAY_INFO_STR_MAX_LEN    | The maximum length, including the NULL terminator, of an information string rendered on top of an overlay. The value of this constant is set to 1024 bytes.                                        |

### VDPOverlayClient Data Types

| **Data Type**     | **Description**        |
| --------- | ----------- |
| VDPOverlayClient_ContextId                | Returned from `VDPOverlayClient.v1.Init()`. This ID is used in every call to the Client API.     |
| VDPOverlay_OverlayId                      | An identifier that represents a local or client-side overlay that doesn't map to a window in the remote desktop. An `OverlayId` can be used in any function that takes a `WindowId`, but a `WindowId` cannot be used as an `OverlayId`.      |
| VDPOverlayClient_OverlayInfo              | This structure is used in the call to `VDPOverlayClient.v1/v2.GetInfo()`. In V1, the first member of `VDPOverlayClient_OverlayInfo` was `cbSize`, which was set by the caller to determine the version of the struct. However, this approach wasn't backward-compatible. For example, a program written to V2 would return an error if it called `GetInfo()` because the size wouldn't be set correctly. Starting with V2, the first member of `VDPOverlayClient_OverlayInfo` is a version and is set by `GetInfo()` to the version of the function that filled the structure. For backward compatibility, when calling `v1.GetInfo()`, the caller must set `version = VDP_OVERLAY_INFO_V1_SIZE` before calling `v1.GetInfo()`. |
| VDPOverlayClient_YUVImageData            | This structure is used in the call to `VDPOverlayClient.v2.Update()` when the image format is a YUV format.                                                                                                                                                                                                                                                                                                                                                                                                |
| **Member**                                | **Description**                                                                                                                                                                                                                                                                                                                                 |
| pImage[3]                                 | An array with a pointer to the pixels for each plane of the image. <br>• BGRX - image[0] = BGRX plane, image[1] = NULL, image[2] = NULL <br>• YUV  - image[0] = Y plane, image[1] = U plane, image[2] = V plane                           |
| pitch[3]                                  | An array with the number of bytes per row for each plane of the image.                      |
| VDPOverlayClient_InfoStringProperties    | This structure is used in the calls to `VDPOverlayClient.v4.GetInfoStringProperties()` and `VDPOverlayClient.v4.SetInfoStringProperties()`. V1 through V3 of `VDPOverlayClient_Interface` do not support this structure. The members of this structure are defined as follows.             |
| **Member**                                | **Description**      |
| v4.enabled                                | A Boolean that activates/deactivates the information string.    |
| v4.fgColor                                | A uint32 specifying the foreground/text color used to render the information string. `0` specifies the default foreground color.   |
| v4.bgColor                                | A uint32 specifying the background color used to render the information string. `0` specifies the default background color.    |
| v4.xBox                                   | An int32 specifying the horizontal distance between the background and the edge of the overlay. Positive numbers position the background on the left. Negative numbers position the background on the right. `0` uses the default margin.                                                                                                                                                                                                                                                                                        |
| v4.yBox                                   | An int32 specifying the vertical distance between the background and the edge of the overlay. Positive numbers position the background on the top. Negative numbers position the background on the bottom. `0` uses the default margin.                                                                                                                                                                                                                                                                                     |
| v4.wBox                                   | An int32 defining the width of the background. Positive numbers denote the maximum width of the background. The text will be scaled to fit in this width using the `LETTERBOX_SHRINK_ONLY` layout mode. Negative numbers denote an absolute width for the background. The text will be scaled to fit in this width using the `LETTERBOX` layout mode. `0` sizes the background to the width of the text.                                                                                                                                                                                                                                      |
| v4.hBox                                   | An int32 defining the height of the background. Positive numbers denote the maximum height of the background. The text will be scaled to fit in this height using the `LETTERBOX_SHRINK_ONLY` layout mode. Negative numbers denote an absolute height for the background. The text will be scaled to fit in this height using the `LETTERBOX` layout mode. `0` sizes the background to the height of the text.                                                                                                                                                                                                                                                                                                       |
| VDPOverlay_LayoutMode                     | This enum represents all of the different layouts that the VDP Overlay API supports.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| VDPOverlay_Error                          | Returned by many of the Overlay functions. Indicates the results that may occur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| VDPOverlay_ImageFormat                    | This enum defines the pixel format of an image passed to `VDPOverlayClient_Interface.v2.Update()`. Note that `VDPOverlayClient_Interface.v1.Update()` always assumes VDP_OVERLAY_BGRX formatted images.       |
                                                                                     
## VDPScreenCapture Data Types

The VDPScreenCapture data types are for use with the Screen Capture API. They are found in `vdpScreenCapture.h`.

### VDPScreenCapture Data Types

| **Data Type**                     | **Description**                                                     |
|-----------------|----------------------------------|
| VDPScreenCapture_ContextId         | Returned from `VDScreenCapture.v1Init()`. This ID is used in every call to the Screen Capture API. `VDP_SCREEN_CAPTURE_ID_NONE` is a value that denotes an invalid `VDPScreenCapture_ContextId`.                    |
| VDPScreenCapture_Rect              | This is used to hold a rectangle.               |
| VDPScreenCapture_HWND              | Type used by the `ReadBackWindow` interface to hold a remote window handle.                        |
| VDPScreenCapture_ReadBackWindowHandle | Returned from `VDPScreenCapture.v3/v4.ReadBackWindowBegin()`. This ID is used when calling `ReadBackWindow` functions. `VDP_SCREEN_CAPTURE_READBACK_WINDOW_HANDLE_NONE` is a value that denotes an invalid `VDPScreenCapture_ReadBackWindowHandle`.                                   
| VDPScreenCapture_ImageHandle       | Returned from `VDPScreenCapture.v2.ReadBackScreen()` or `v3.ReadBackWindow()` to refer to the image returned. `VDP_SCREEN_CAPTURE_IMAGE_HANDLE_NONE` is a value that denotes an invalid `VDPScreenCapture_ImageHandle`.                                                                                                    |
| VDPScreenCapture_ReadBackRequestId | Returned from `VDPScreenCapture.v4.RegisterForReadBackRequests()`. `VDP_SCREEN_CAPTURE_READBACK_REQUEST_ID_NONE` is a value that denotes an invalid `VDPScreenCapture_ReadBackRequestId`.               |
| VDPScreenCapture_ImageFormat       | Used to denote the format of an image returned from the `VDPScreenCapture` interface.                                    |
| **Member**                         | **Description**                                                                                                            |
| VDP_SCREEN_CAPTURE_BGRX            | 32-bit RGB image. The high byte is ignored.                                                                            |
| VDP_SCREEN_CAPTURE_YUVI420         | YUV I420 image.                                                                                                          |
| VDPScreenCapture_OverlayOptions    | Determines how overlays are handled during a screen capture.                                                           |
| **Member**                         | **Description**                                                                                                          |
| VDP_SCREEN_CAPTURE_OVERLAY_INCLUDE_ALL   | The image includes all overlays.                                                                                        |
| VDP_SCREEN_CAPTURE_OVERLAY_EXCLUDE_ALL   | The image excludes all overlays.                                                                                       |
| VDP_SCREEN_CAPTURE_OVERLAY_EXCLUDE_FLAGGED | The image will exclude overlays marked with `VDP_OVERLAY_UPDATE_FLAG_EXCLUDE_FROM_READ_BACK` in the call to `VDPOverlayClient_Interface.v2.Update()`.      |

### VDP_SCREEN_CAPTURE_TOPOLOGY_CHANGED Flags

Flags that can be passed to topology changed callback registered via `VDPScreenCapture_Sink.v1.OnTopologyChanged()`. One or more of these flags will be set when the function is called.

| Flag                                          | Description                                                                 |
|----------------------------------------------|-----------------------------------------------------------------------------|
| `VDP_SCREEN_CAPTURE_LOCAL_TOPOLOGY_CHANGED`  | Denotes that the local topology has changed.                               |
| `VDP_SCREEN_CAPTURE_REMOTE_TOPOLOGY_CHANGED` | Denotes that the remote topology has changed.                              |
| `VDP_SCREEN_CAPTURE_HOST_WINDOWID_CHANGED`   | Denotes that the OS window ID of the Horizon Client window has changed.    |

# VDP_SCREEN_CAPTURE_READBACK_CAPS Flags

Flags returned from `VDPScreenCapture.v4.GetReadBackCapabilities()`.

| Flag                                                     | Description                                                                 |
|----------------------------------------------------------|-----------------------------------------------------------------------------|
| `VDP_SCREEN_CAPTURE_READBACK_CAPS_READBACK_SCREEN`       | Set if `v2.ReadBackScreen()` is available.                                 |
| `VDP_SCREEN_CAPTURE_READBACK_CAPS_READBACK_WINDOW`       | Set if `v3.ReadBackWindow()` is available.                                 |
| `VDP_SCREEN_CAPTURE_READBACK_CAPS_VISIBLE_AREA_ONLY`     | Set if `v3.ReadBackWindow()` with `VISIBLE_AREA_ONLY` is available.        |
| `VDP_SCREEN_CAPTURE_READBACK_CAPS_AUXILIARY_WINDOWS`     | Set if `v4.ReadBackWindowBegin()` with auxiliary windows is available.     |

# VDP_SCREEN_CAPTURE_READBACK_BEGIN Flags

Flags that can be passed to `VDPScreenCapture_Interface.v3/v4.ReadBackWindowBegin()`.

| Flag                                                  | Description                                                                                                                               |
|-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `VDP_SCREEN_CAPTURE_READBACK_BEGIN_VISIBLE_AREA_ONLY` | Clips the non-visible area of the window. The area of the window that is obscured by other windows is also obscured in the returned image.|
| `VDP_SCREEN_CAPTURE_READBACK_BEGIN_LOCATION_CHANGED`  | Set if you want to be notified when the location of the readback window changes. Only a single event is queued at a time.                |
| `VDP_SCREEN_CAPTURE_READBACK_BEGIN_LOCATION_CHANGED_EX`| Set to be notified on every location update. Generates more events but gives a more accurate movement path.                             |
| `VDP_SCREEN_CAPTURE_READBACK_BEGIN_IMAGE_CHANGED`     | Set if you want to be notified when the image of the readback window changes.                                                             |

# VDP_SCREEN_CAPTURE_READBACK Flags

Flags that can be used in `VDPScreenCapture_ReadBackParameters.v3.flags`.

| Flag                                              | Description                                                                                                                           |
|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| `VDP_SCREEN_CAPTURE_READBACK_MAINTAIN_ASPECT_RATIO` | Maintain the aspect ratio when scaling.                                                                                              |
| `VDP_SCREEN_CAPTURE_READBACK_SHRINK_ONLY`          | `scaledWidth/Height` represents a max size. Scaling occurs only if image size exceeds that.                                           |
| `VDP_SCREEN_CAPTURE_READBACK_RETURN_TEST_IMAGE`    | Returns a solid color test image.                                                                                                     |
| `VDP_SCREEN_CAPTURE_READBACK_WRITE_IMAGE_FILE`     | Writes the returned image to a file:                                                                                                  |
|                                                   | - `ReadBackScreen` → `%TEMP%\ReadBackScreen.png`                                                                                      |
|                                                   | - `ReadBackWindow` → `%TEMP%\ReadBackWindow-<ID>.png`                                                                                 |

# VDPScreenCapture_ReadBackParameters

Structure used in the call to `VDPScreenCapture_Interface.v2.ReadBackScreen()` and `VDPScreenCapture_Interface.v3.ReadBackWindow()`.

| Field                               | Description                                                                                                                                                                  |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uint32 version`                    | Set the version number: `VDP_SCREEN_CAPTURE_READ_BACK_PARAMETERS_V2` or `VDP_SCREEN_CAPTURE_READ_BACK_PARAMETERS_V3`                                                        |
| `VMRect v2.srcRect`                | Area within the remote desktop or window to read. Set all 0s to read the entire screen or window.                                                                            |
| `VDPScreenCapture_ImageFormat v2.format` | Format of the returned image.                                                                                                                                            |
| `VDPScreenCapture_OverlayOptions v2.overlayOptions` | Determines overlays to include.                                                                                                                                    |
| `bool v2.includeCursor`             | Determines if cursor is included in the read back.                                                                                                                           |
| `int32 v2.scaledWidth`, `v2.scaledHeight` | Scaled size of returned image. No scaling if either is 0.                                                                                                                    |
| `int32 v2.alignment`                | Alignment requirements in bytes. Each scanline pointer is aligned to a multiple of this. 0 = don't care.                                                                   |
| `uint32 v3.flags`                   | See `VDP_SCREEN_CAPTURE_READBACK` flag definitions.                                                                                                                          |

# VDPScreenCapture_ImageInfo

Structure used in the call to `VDPScreenCapture_Interface.v2.ReadBackScreen()`.

| Field                                | Description                                                                                      |
|--------------------------------------|--------------------------------------------------------------------------------------------------|
| `uint32 version`                     | Set the version number: `VDP_SCREEN_CAPTURE_IMAGE_INFO_V2`, `VDP_SCREEN_CAPTURE_IMAGE_INFO_V4` |
| `VDPScreenCapture_ImageHandle v2.hImage` | Handle passed to `ReadBackRelease()` to release resources.                                   |
| `void* v2.image[3]`                  | Pixel pointers:                                                                                  |
|                                      | - BGRX → `image[0] = BGRX`, `image[1,2] = NULL`                                                  |
|                                      | - YUV  → `image[0] = Y`, `image[1] = U`, `image[2] = V`                                          |
| `int32 v2.pitch[3]`                  | Number of bytes per row for each image plane.                                                    |
| `int32 v2.width`, `v2.height`        | Width and height of the image.                                                                   |
| `VDPScreenCapture_ImageFormat v2.format` | Format of the image.                                                                          |
| `VMRect v4.location`                | Location on remote desktop (in remote topology coordinates) used to read back the image.         |

# VDPScreenCapture_ReadBackWindowInfo

Structure used in the call to `VDPScreenCapture_Interface.v4.GetReadBackWindowInfo()`.

| Field                                     | Description                                                                                       |
|------------------------------------------|---------------------------------------------------------------------------------------------------|
| `uint32 version`                         | Set the structure version: `VDP_SCREEN_CAPTURE_READBACK_WINDOW_INFO_V4`                          |
| `VDPScreenCapture_ReadBackWindowHandle v4.hReadBackWindow` | Handle for the readback window.                                                           |
| `VDPScreenCapture_RemoteError v4.state`  | Current state of the readback window.                                                              |
| `VDPScreenCapture_HWND v4.hWnd`          | Window handle.                                                                                     |
| `uint32 v4.processId`                    | Process ID for the window.                                                                         |
| `uint32 v4.flags`                        | Parameters passed to `ReadBackWindowBegin()`.                                                      |
| `const VDPScreenCapture_HWND* v4.hWndAux` | Auxiliary window handles.                                                                        |
| `const uint32* v4.processIdAux`         | Auxiliary process IDs.                                                                             |
| `int32 v4.auxWindowCount`               | Number of auxiliary windows.                                                                       |
| `VMRect v4.location`                    | Location on the remote desktop, in remote topology coordinates.                                    |

# VDPScreenCapture_ReadBackRequestParams

Structure used in the call to `VDPScreenCapture_Interface.v4.ReadBackRequestUpdate()`.

| Field                                 | Description                                                                                          |
|--------------------------------------|------------------------------------------------------------------------------------------------------|
| `uint32 version`                     | Set to `VDP_SCREEN_CAPTURE_READBACK_REQUEST_INFO_V4`                                                |
| `void* v4.image[3]`                  | Pixel pointers:                                                                                      |
|                                      | - BGRX → `image[0] = BGRX`, `image[1,2] = NULL`                                                      |
|                                      | - YUV  → `image[0] = Y`, `image[1] = U`, `image[2] = V`                                              |
| `int32 v4.pitch[3]`                  | Number of bytes per row for each plane.                                                              |
| `int32 v4.width`, `v4.height`        | Width and height of the image.                                                                       |
| `VDPOverlay_ImageFormat v4.format`   | Image format, must be supported by the VDPOverlay API.                                               |
| `VDPOverlay_LayoutMode v4.layoutMode`| Layout mode of overlay, defines how image scales to destination.                                     |
| `uint32 v4.layer`                    | Overlay layer. Higher value = overlay on top.                                                        |
| `int32 v4.clipRgnNRects`             | Number of clip region rectangles.                                                                    |
| `VDPScreenCapture_Rect* v4.clipRgnRects` | Clip region array (in image coordinates). NULL if not used.                                      |
| `VMRect v4.dstRect`                 | Area within the remote desktop to place the image. Top-left is (0,0).                                |
| `uint32 v4.imageFlags`              | Flags used when updating the image. See `VDP_OVERLAY_UPDATE_FLAG` in `vdpOverlay.h`.                 |


## Error Codes

The Horizon Session Enhancement API specifies codes to indicate errors.

### RPC OnAbort Reason Error Codes

If the call to the `VDPRPC_ChannelObjectInterface.v1.OnInvoke()` method fails due to a Horizon Session Enhancement error, the supplied `OnAbort` method is called and the last parameter to this method contains one of the following error codes.

| Code | Description |
| ---- | ----------- |
| VDP_RPC_E_APARTMENT_UNINITIALIZED | This error occurs if the `OnInvoke` call is made on a thread that is not initialized to be used with the Horizon Session Management API. |
| VDP_RPC_E_APARTMENT_THREAD | This error occurs if the `OnInvoke` call involves an object that was not created on the calling thread and the object is not configured to allow `OnInvoke` calls on different threads. |
| VDP_RPC_E_OBJECT_NOT_CONNECTED | This error occurs if the object handle that is used for the `OnInvoke` call points to an object that is not connected. This error indicates that the peer object on the remote side is not yet created. |
| VDP_RPC_E_PARAMETER | One of the required parameters that is passed to the `OnInvoke` call is invalid. |
| VDP_RPC_E_MEMORY | The system fails to allocate the required memory to send the request. |

### VDPOverlay_Error Codes

If an error occurs, many of the methods that are defined in `vdpOverlay.h` return one of the following errors.

| Code | Description |
| ---- | ----------- |
| VDP_OVERLAY_ERROR_SUCCESS | No error. The call is successful. |
| VDP_OVERLAY_ERROR_NOT_INITIALIZED | The call fails because the VDP Overlay components are not properly loaded in the Horizon environment. |
| VDP_OVERLAY_ERROR_ALREADY_INITIALIZED | This error is only returned from the `VDPOverlayGuest_Interface.v1.Init()` call. The guest Overlay system is already initialized. |
| VDP_OVERLAY_ERROR_INVALID_PARAMETER | One of the required parameters that is passed to the call is invalid. |
| VDP_OVERLAY_ERROR_ALLOCATION_ERROR | The system fails to allocate the required memory or system resource to handle the call. |
| VDP_OVERLAY_ERROR_NO_MORE_OVERLAYS | This error results from a failed attempt to register a window and may be received in the `VDPOverlayGuest_Sink.v1.OnOverlayCreateError()` or `VDPOverlayClient.v2.CreateOverlay()` callback. This error may be due to a client-side error. It can also occur if the call tries to register a window that is already registered with a different plug-in. |
| VDP_OVERLAY_ERROR_OVERLAY_REJECTED | This error results from a failed attempt to register a window and is returned in the reason field of the `VDPOverlayGuest_Sink.v1.OnOverlayRejected()` callback. This error occurs if the client does not accept the overlay registration request. |
| VDP_OVERLAY_ERROR_OVERLAY_NOT_READY | This error occurs when either `VDPOverlayGuest_Interface.v1.EnableOverlay` or `VDPOverlayGuest_Interface.v1.DisableOverlay` fails. It indicates that the registered window is not ready, that is, the `VDPOverlayGuest_Sink.v1.OnOverlayReady()` callback is not yet received. |
| VDP_OVERLAY_ERROR_WINDOW_NOT_REGISTERED | The window ID that is specified in the call is not yet registered. Many Overlay methods may return this error. |
| VDP_OVERLAY_ERROR_WINDOW_ALREADY_REGISTERED | The window is already registered. This error can be returned from the `VDPOverlayGuest_Interface.v1.RegisterWindow()` method. |
| VDP_OVERLAY_ERROR_NOT_LOCAL_OVERLAY | The overlayId of a guest-side overlay was passed to a function that can only be called on a local overlay. |
| VDP_OVERLAY_ERROR_HOST_OVERLAY_ERROR | There is an error with a low level library. This error code should be treated as similar to INVALID_PARAMETER. |
| VDP_OVERLAY_ERROR_NOT_SUPPORTED_BY_CLIENT | The version of the client-side VDP Overlay API does support the feature. |

## VDPScreenCapture_Error Codes

If an error occurs, many of the methods that are defined in `vdpScreenCapture.h` return one of the following errors.

### VDPScreenCapture_Error Codes

| Code      | Description      |
|----------------------|--------|
| `VDP_SCREEN_CAPTURE_ERROR_SUCCESS`            | No error. The call is successful.                                                                                                                                      |
| `VDP_SCREEN_CAPTURE_ERROR_HOST_NOT_READY`     | The call failed because the Screen Capture API is not done initializing.                                                                                             |
| `VDP_SCREEN_CAPTURE_ERROR_HOST_VERSION_ERROR` | This error is only if the version of `vdpService.dll` is not matched with the version of the Horizon client. This can only happen if the version of `vdpService.dll` being used is not the version that shipped with Horizon. |
| `VDP_SCREEN_CAPTURE_ERROR_HOST_ERROR`         | There is an error with a low-level library. This error code should be treated as similar to `INVALID_PARAMETER`.                                                      |
| `VDP_SCREEN_CAPTURE_ERROR_INVALID_PARAMETER`  | One of the parameters passed into a function is not valid.                                                                                                           |
| `VDP_SCREEN_CAPTURE_ERROR_ALLOCATION_ERROR`   | The system fails to allocate the required memory or system resource to handle the call.                                                                               |
| `VDP_SCREEN_CAPTURE_ERROR_NOT_ALLOWED_IN_APP_MODE` | Many of the functions in the Screen Capture API cannot be used when the Horizon client is remoting a single application. They can only be used when remoting the entire desktop. |
| `VDP_SCREEN_CAPTURE_ERROR_READBACK_WINDOW_NOT_READY` | The `ReadBackWindow` interface must initialize with the Horizon Agent on the remote desktop before it is ready.                                                          |
| `VDP_SCREEN_CAPTURE_ERROR_READBACK_WINDOW_DESTROYED` | The `ReadBackWindow` interface is tracking a window that no longer exists on the remote desktop.                                                                       |
| `VDP_SCREEN_CAPTURE_ERROR_UNSUPPORTED`        | The function that you are trying to use is not supported.                                                                                                             |
| `VDP_SCREEN_CAPTURE_ERROR_UNSUPPORTED_PROTOCOL` | The function is not supported by the protocol. The `ScreenCapture` and `ReadBackWindow` interfaces are only supported by the Blast protocol.                           |
| `VDP_SCREEN_CAPTURE_ERROR_UNSUPPORTED_AGENT`  | The function is not supported by the Horizon Agent on the remote desktop. This is usually because the version of the Horizon Agent does not support the `ReadBackWindow` interface. |
| `VDP_SCREEN_CAPTURE_ERROR_UNSUPPORTED_OPTION` | When calling `v3.ReadBackWindow()`, one of the options in the `flags` parameter is not supported by the Horizon Client.          |

## VDPScreenCapture_RemoteError Codes

List of all possible error codes for `VDPScreenCapture_Sink.v3.OnReadBackWindowRemoteError()`.

### VDPScreenCapture_RemoteError Codes

| Code                                              | Description                                                                                                             |
|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_WINDOW_READY`     | No error. The remote window tracking is ready to return images.                                                           |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_WINDOW_NOT_READY` | The remote window tracking failed because the Horizon Agent isn't ready to return images.                               |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_WINDOW_DESTROYED` | The remote window tracking failed because the remote window was destroyed.                                               |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_TRACKING_FULL`    | The remote window tracking failed because the Horizon Agent is tracking too many windows.                               |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_INVALID_WINDOW`   | The remote window tracking failed because the requested window does not exist.                                           |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_INVALID_PID`      | The remote window tracking failed because the requested window does not belong to the process specified.                 |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_UNSUPPORTED`      | The remote window tracking failed because the Horizon Agent does not support a requested capability.                     |
| `VDP_SCREEN_CAPTURE_REMOTE_ERROR_CAPTURE_FAILED`   | The remote window tracking failed because the window on the remote desktop could not be captured.                        |

