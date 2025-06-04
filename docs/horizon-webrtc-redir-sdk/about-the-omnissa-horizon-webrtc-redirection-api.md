# About the Omnissa Horizon WebRTC Redirection API

The Omnissa Horizon WebRTC Redirection API specifies how the client side and the desktop side of an Electron application can communicate over a Horizon connection to accomplish WebRTC-based media redirection. Most of the interactions with the API are asynchronous.

## Application Software Components

Any Electron software that uses the Horizon WebRTC Redirection API must include:

- The Electron application itself
- Horizon SDK for WebRTC Redirection, installed as JavaScript code in the application

> Throughout this document, “Application” refers to the Electron-based app using the SDK.

## Horizon WebRTC Redirection API Components

- **Basic WebRTC APIs**: Provide calls to retrieve the media device list and capture local streams.
- **Teleconnection APIs**: Provide functionality similar to W3C peer-to-peer communications APIs. See [W3C WebRTC API](https://www.w3.org/TR/webrtc/#peer-to-peer-connections).
- **MediaStream APIs**: Align with standard Web MediaStream APIs. See [MDN MediaStream docs](https://developer.mozilla.org/en-US/docs/Web/API/MediaStream).

## Supported Versions of Horizon Software

To work with the Horizon SDK for WebRTC Redirection, your Horizon deployment must meet certain system and setup requirements. For detailed information, see the "Omnissa Horizon SDK for WebRTC Redirection Setup Guide".


