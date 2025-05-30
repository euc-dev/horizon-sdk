---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# Sample Application Setup

The Horizon SDK includes a **sample Electron application** that demonstrates how to implement WebRTC Redirection. You can use it as a reference or as a starting point for your own UC (unified communication) application.

---

## Prerequisites

Before running the sample application:

- Ensure Horizon Agent is installed and configured on the remote desktop.
- Ensure Horizon Client is installed and that WebRTC Redirection is enabled.
- Confirm that group policies or registry settings are correctly configured to allow Electron-based optimization.
- Ensure Node.js and npm are installed on the virtual desktop.

---

## Installation

The SDK zip file contains a `sample` directory. Follow these steps to install and run the sample app:

```bash
cd webrtcredir/sample
npm install
```

> 📦 The `package.json` file defines all required dependencies.

---

## Launching the Sample App

To start the application:

```bash
npm start
```

A new Electron window will open and attempt to connect to the Horizon WebRTC Redirection backend.

- If the status label turns **green**, redirection is active.
- If it remains **red**, redirection is not enabled and the fallback (RTAV) path will be used.

---

## Debug Logging

To enable verbose logs during development, modify the launch script to set an environment variable:

```bash
DEBUG=webrtcredir:* npm start
```

This will output detailed SDK logs in the console, helpful for troubleshooting initialization and API usage.

---

## File Structure Overview

```text
sample/
├── main.js           # Main process code
├── preload.js        # Preload script that injects SDK APIs
├── renderer.js       # Renderer process and UI logic
├── index.html        # App window UI
├── webrtcredir/      # SDK integration files
├── package.json      # NPM project config
```

---

## Notes

- You may need to relax Electron security settings (`contextIsolation`, `nodeIntegration`) to allow full SDK access during development.
- For production apps, isolate SDK usage to preload scripts and use strict context bridging to reduce attack surface.

