---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

The Omnissa Horizon® SDK for WebRTC Redirection provides access to interfaces that WebRTC-based UC vendors can use to leverage the Media Optimization feature of Horizon Client and Horizon remote desktops. The SDK enables the offloading of audio, video, and screenshare content to the local client system.

This SDK is free and public. To obtain technical support for the use of the SDK, please submit a Support Request (SR) via [Omnissa Customer Connect](https://customerconnect.omnissa.com/home) to get help from the Omnissa Global Customer Services (GCS).

## Downloads

Omnissa provides this Software Development Kit (the “Software”) to you subject to the following terms and conditions. By downloading, installing, or using the Software, you agree to be bound by the terms of [Omnissa SDK License Agreement](https://static.omnissa.com/sites/default/files/omnissa-sdk-agreement.pdf). If you disagree with any of the terms, then do not use the Software.

For additional information, please visit the [Omnissa Legal Center](https://www.omnissa.com/legal-center/).

The SDK is provided as either a [Package](https://github.com/orgs/euc-releases/packages?repo_name=horizon-rdpbridge-sdk) or [Release](https://github.com/euc-releases/horizon-rdpbridge-sdk/releases). Please download the software from the appropriate location.

## License

This software is licensed under the [Omnissa Software Development Kit (SDK) License Agreement](https://static.omnissa.com/sites/default/files/omnissa-sdk-agreement.pdf); you may not use this software except in compliance with the License.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

This software may also utilize Third-Pary Open Source Software as detailed within the [open_source_licenses.txt](open_source_licenses.txt) file.

## Documentation and Reference

| Name | Size	|
| --- | --- |
| Development Guides |  |
| [Omnissa Horizon SDK for WebRTC Redirection Programming Guide](./horizon_sdk_for_webrtc_redirection_programming_guide_2025-05-30-05-45-41.pdf) | 249 KB |


- [Introduction](introduction.md) 
- [About the Omnissa Horizon WebRTC Redirection API](about-the-omnissa-horizon-webrtc-redirection-api.md)
- [Horizon SDK for WebRTC Redirection Program Flow](horizon-sdk-for-webrtc-redirection-program-flow.md) 
- [Basic WebRTC API Reference](basic-webrtc-api-reference.md) 
    - [enumerateDevices()](enumerateDevices().md)
    - [getCallConfig(index)](getCallConfig(index).md)
    - [getDisplayMedia(constraints)](getDisplayMedia(constraints).md) 
    - [getReceiverCapabilities(kind)](getReceiverCapabilities(kind).md)
    - [getScreenInfo()](getScreenInfo().md) 
    - [getUserMedia (constraints)](getUserMedia(constraints).md)
    - [initSDK (appLogger, appName, eventCallback)](initSDK(appLogger,appName,eventCallback).md)
    - [isFeatureSupported (feature)](isFeatureSupported(feature).md) 
    - [newMediaStream(tracks)](newMediaStream(tracks).md) 
    - [newPeerConnection(configuration)](newPeerConnection(configuration).md) 
    - [onAudioCreated(audioElem, window)](onAudioCreated(audioElem,window).md) 
    - [onAudioDisposed(audioElem)](onAudioDisposed(audioElem).md) 
    - [onScreenSelected(screenId)](onScreenSelected(screenId).md) 
    - [onVideoCreated(videoElem, window)](onVideoCreated(videoElem,window).md)
    - [onVideoDisposed(videoElem)](onVideoDisposed(videoElem).md) 
    - [onWindowSessionConnected(state)](onWindowSessionConnected(state).md)
    - [pauseRingtone(id)](pauseRingtone(id).md) 
    - [playRingtone(id,src,isLoop)](playRingtone(id,src,isLoop).md) 
    - [setPrimarySinkId(sinkId)](setPrimarySinkId(sinkId).md) 
    - [setSinkId(id,sinkId)](setSinkId(id,sinkId).md) 
    - [setVideoClipRegion (isAdd,clipRegion,window)](setVideoClipRegion(isAdd,clipRegion,window).md) 
- [Setting Up the Sample Application](setting-up-the-sample-application.md) 
    - [Set Up the Web Server (https)](set-up-the-web-server(https).md) 
    - [Set Up the Web Socket Server (WSS)](set-up-the-web-socket-server(wss).md)
    - [Configure the Client and Run the App](configure-the-client-and-run-the-app.md) 
    - [Make a Test Meeting Call](make-a-test-meeting-call.md) 
