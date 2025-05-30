---
layout: page
title: Horizon webRTC Redirection SDK
hide:
  #- navigation
  - toc
---
# Omnissa Horizon RDP Virtual Channel Bridge SDK Programming Guide

For Horizon 7, Horizon 8, and Horizon Cloud Service

Omnissa Horizon RDP Virtual Channel Bridge SDK 4.0

You can find the most up-to-date technical documentation on the Omnissa website at [https://docs.omnissa.com/](https://docs.omnissa.com/).

This guide provides information about developing applications using Microsoft Windows Remote Desktop Services (RDS) virtual channels on Omnissa Horizon.

With the virtual channel enhancements, the server and client components of the applications can communicate over the PCoIP and Blast virtual channels, in addition to the Remote Desktop Protocol (RDP) virtual channels, with minimal changes to the applications.

## Intended Audience

This document is intended for third-party software developers who want to enhance the functionality of their applications that run on virtual desktops provisioned by Omnissa Horizon 7, Omnissa Horizon 8, or Omnissa Horizon Cloud Service. With the enhancements, the RDS virtual channels can provide a better user experience because the applications can run over PCoIP and Blast virtual channels.

**NOTE**: Within this document, file paths, registry keys, and similar code-related items are revised to reflect the SDK's 
use with the Omnissa stack. References to items that were for Horizon versions 2406 and earlier versions contain 
asterisks (***) to redact the previous name. 

## Introduction

Microsoft Windows Remote Desktop Services (RDS), previously known as Terminal Services (TS), is a set of software services that gives a user access to applications or desktops over a network. RDS uses the desktop remoting protocol, Remote Desktop Protocol (RDP). Omnissa Horizon supports RDP, PCoIP and Blast protocols, to provide a user with the remote access capability. PCoIP and Blast protocols provide an optimized desktop experience for the delivery of the entire desktop environment, including applications, images, audio, and video content.

RDP, PCoIP, and Blast support a feature called a virtual channel, which is a software extension to an RDS application. A virtual channel has a server and a client component. With virtual channels, you can add user experience enhancements to RDS applications without changing the client or server software, or the display protocol.

There are many third-party off-the-shelf plug-ins that are written for RDP virtual channels. Converting these plug-ins to work over PCoIP or Blast require a significant effort. In addition, it becomes necessary to maintain two versions of the plug-in, one for each protocol. The Omnissa Horizon RDP Virtual Channel Bridge, also called RDPVCBridge, helps solve both of these problems by providing a bridge between the RDP virtual channels and the PCoIP or Blast virtual channels. With RDPVCBridge, an application can work over the RDP, PCoIP, or Blast protocols. RDPVCBridge detects whether the application is running in an RDP, PCoIP, or Blast context and determines which protocol to use accordingly.

## Benefits of Using the RDPVCBridge SDK

RDS provides the Windows Terminal Services (WTS) API for virtual channels. Omnissa PCoIP or Horizon Blast provides a different API for virtual channels. Without the RDPVCBridge SDK, you must rewrite RDP virtual channel plug-ins to use the PCoIP or Blast virtual channel API. The effort to rewrite the plug-ins can be significant. The RDPVCBridge SDK makes it much easier to enhance RDS virtual channel applications to support RDP and PCoIP or Blast.

## What's New in Omnissa Horizon RDP Virtual Channel Bridge SDK 4.0

The following list summarizes the new features and changes found in version 4.0 of the Omnissa Horizon RDP Virtual Channel Bridge SDK.

- This version of the SDK adds support for the new Omnissa-branded stack and also has backward the older version as fallback. 

- Make files for Linux and Mac are supplied with the sample.

## Supported Platforms and Applications

The RDPVCBridge SDK supports multiple platforms and applications.

- The RDPVCBridge SDK was first released in 2013 and supports all versions of Horizon 7 and Horizon 8 that have been released since then. The RDPVCBridge SDK also supports Horizon Cloud Service on Microsoft Azure.

- The RDPVCBridge SDK supports all versions of Windows, Linux, and Mac clients that Horizon supports. 

- The RDPVCBridge SDK does not support Zero clients.

## Contents

- [Virtual Channel Security](VirtualChannelSecurity.md)
- [How to Use RDPVC Bridge SDK](HowtoUseRDPVCBridgeSDK.md)
- [RDPVC Bridge SDK Source Files](RDPVCBridgeSDKSourceFiles.md)
- [Remote Desktop Services API Support](RemoteDesktopServicesAPISupport.md)

- Client-Side API Function
  - [`VDP_IsNestedClient`](VDP_IsNestedClient.md)
- Agent-side API Functions
  - [`VDP_GetSDKVersion`](VDP_GetSDKVersion.md)
  - [`VDP_IsLegacyHorizonInstalled`](VDP_IsLegacyHorizonInstalled.md)
  - [`VDP_IsHorizonSession`](VDP_IsHorizonSession.md)
  - [`VDP_IsBlastSession`](VDP_IsBlastSession.md)
  - [`VDP_IsPCoIPSession`](VDP_IsPCoIPSession.md)
  - [`VDP_IsRDPSession`](VDP_IsRDPSession.md)
  - [`VDP_IsDesktopSession`](VDP_IsDesktopSession.md)
  - [`VDP_IsApplicationSession`](VDP_IsApplicationSession.md)
  - [`VDP_IsNestedSession`](VDP_IsNestedSession.md)

- [Dynamic Virtual Channel API Support](DynamicVirtualChannelAPISupport.md)
- [Sample Virtual Channel Application](SampleVirtualChannelApplication.md)

- [Setting up `vchan-ping` on the Client](Settingupvchan-pingontheClient.md)
- [Setting up 'vchan-ping' on the Agent](Settingupvchan-pingontheAgent.md)

- [Debugging and Collecting Logs](DebuggingandCollectingLogs.md)
  - [Windows](Windows.md)
  - [Linux](Linux.md)
  - [Mac](MacOSX.md)

- [Setting Up a Developer Environment Using VADC](SettingupaDeveloperEnvironmentUsingVADC.md)
- [Software Requirements](SoftwareRequirements.md)
- [How Components are Delivered and Supported](HowComponentsareDeliveredandSupported.md)
- [Support Policy](SupportPolicy.md)