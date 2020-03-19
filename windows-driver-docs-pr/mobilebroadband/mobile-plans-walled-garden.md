---
title: Mobile Plans walled garden
description: Mobile Plans walled garden
ms.assetid: fb1566c6-8d47-4aa9-93f4-415ef7070ac6
keywords:
- Windows Mobile Plans mobile operators walled garden
ms.author: windowsdriverdev
ms.date: 07/31/2019
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
---

# Mobile Plans walled garden

The Mobile Plans *Walled Garden* is key to supporting customers when they run out of data. It enables them to reach the MO Direct portal even when there is no alternative internet connection such as Wi-Fi. This will enable consumers to purchase additional data plans and manage their subscriptions.

> [!NOTE]
> The Mobile Plans architecture does not support IP ranges for Walled Garden endpoints. Host names must be used for whitelisting.

The MO Direct web portal and `GetBalance` API endpoint must also be part of this Walled Garden.

## Walled Garden endpoints

There are only a small number of required endpoints that are always accessible to end users. The following table defines the endpoints required for Walled Garden.

| URL | HTTP/HTTPS |
| --- | --- |
| service.datamart.windows<span></span>.com | https |
| dogfood.datamart.windows<span></span>.com | https |
| windows.policies.live<span></span>.net | https |
| ctldl.windowsupdate<span></span>.com | http |
| cdp1.public-trust<span></span>.com | http |
| ocsp.omniroot<span></span>.com | http |
| vassg142.ocsp.omniroot<span></span>.com | http |
| vassg142.crl.omniroot<span></span>.com | http |
| mscrl.microsoft<span></span>.com | http |
| crl.microsoft<span></span>.com | http |
| www.msftconnecttest<span></span>.com | http |
| crl3.digicert<span></span>.com | http |
| Ocsp.digicert<span></span>.com | http |
| login.live<span></span>.com | http + https |
| storagetos.datamart.windows<span></span>.com | http + https |
| mps.datamart.windows<span></span>.com | http + https |
| mps-service.datamart.windows<span></span>.com | http + https |
| staging.datamart.windows<span></span>.com | http + https |
| mps-staging.datamart.windows<span></span>.com | http + https |
