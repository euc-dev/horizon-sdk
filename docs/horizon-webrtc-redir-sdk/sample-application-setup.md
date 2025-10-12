---
layout: page
title: Sample Application Setup
hide:
  #- navigation
  - toc
---

The Horizon SDK includes both a **sample Electron application** and a **sample web application** that demonstrate how to implement WebRTC Redirection. You can use it as a reference or as a starting point for your own UC (unified communication) application.

---

## Prerequisites

Before running the sample application:

- Ensure Horizon Agent is installed and configured on the remote desktop.
- Ensure Horizon Client is installed and that WebRTC Redirection is enabled.
- Confirm that group policies or registry settings are correctly configured to allow Electron-based optimization for Electron sample app.
- Confirm that group policies or registry settings are configured and the Horizon WebRTC SDK browser extension is added to the chrome browser to allow optimization for the web sample app.
- Ensure Node.js and npm are installed on the virtual desktop.

---

## Installation

Download the SDK and Sample App from [Github](https://github.com/euc-releases/horizon-webrtc-redir-sdk)

---

## Setting up the Sample App

Please refer to the instructions in `horizon-webrtc-redir-sdk/Sample/README` to set up the Electron based sample app or the Web based sample app.

Refer to `horizon-webrtc-redir-sdk/SDK/README` for instructions on how to install and use the SDK.

When the sample app attempts to connect to the Horizon WebRTC redirection backend:
- If the status label turns **green**, redirection is active.
- If it remains **red**, redirection is not enabled.

---

## Notes

- You may need to relax Electron security settings (`contextIsolation`, `nodeIntegration`) to allow full SDK access during development.
- For production apps, isolate SDK usage to preload scripts and use strict context bridging to reduce attack surface.
