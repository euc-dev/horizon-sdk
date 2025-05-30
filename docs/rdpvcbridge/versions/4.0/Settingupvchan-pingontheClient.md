---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---

# Setting up `vchan-ping` on the Client

## On Windows systems

- Build `vchan-ping-client.dll` using the Visual Studio solution file.
- Copy the file `vchan-ping-client.dll` to the client.
- Register the DLL using the following command:  
  `regsvr32.exe vchan-ping-client.dll`

## On Linux systems

- Build `libvchanpingclient.so` using the supplied Makefile.
- Copy the file `libvchanpingclient.so` to the appropriate folder (the Makefile may have already done this):
  - Client versions 2412 and later: `~/.omnissa/rdpvcbridge` or `/lib/.omnissa/rdpvcbridge`
  - Client versions 2406 and earlier: `~/.*****/rdpvcbridge` or `/lib/.*****/rdpvcbridge`

## On Mac systems

- Build `libvchanpingclient.dylib` using the supplied Makefile.
- Copy the file `libvchanpingclient.dylib` to the appropriate folder (the Makefile may have already done this):
  - Client versions 2412 and later: `~/.omnissa/rdpvcbridge` or `/Library/.omnissa/rdpvcbridge`
  - Client versions 2406 and earlier: `~/.*****/rdpvcbridge` or `/Library/.*****/rdpvcbridge`