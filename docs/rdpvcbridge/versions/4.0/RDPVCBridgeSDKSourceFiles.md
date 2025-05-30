---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# RDPVCBridge SDK Source Files

The RDPVCBridge SDK contains the following source files.

- **vdp_rdpvcbridge.h** - The header file that maps WTS function calls to VDP_ function calls.

- **vdp_rdpvcbridge_import.cpp** - C++ source code for the import library that you can use with your application.

The `vdp_rdpvcbridge.dll` file is delivered with Horizon on both the agent and client sides. Use the version of `vdp_rdpvcbridge.dll` that is included with Horizon Agent and Horizon Client. Do not use the versions of `vdp_rdpvcbridge.dll` that came with previous versions of the RDPVCBridge SDK.
