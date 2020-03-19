---
title: Previous WDK versions and other downloads
description: Install versions of the Windows Driver Kit (WDK), the Windows Debugger (WinDBG), and more.
ms.assetid: e07d9f05-f8d0-46e5-82e6-c23baa614bb1
keywords:
- Windows Driver Kit
- previous versions
- WDK
ms.date: 05/07/2018
ms.localizationpriority: medium
ms.custom: 19H1
---

# Other WDK downloads

This topic contains information about earlier versions of the Windows Driver Kit (WDK),
Enterprise WDK (EWDK), and additional downloads for support purposes. To develop drivers,
use the latest public versions of the Windows Driver Kit (WDK) and tools, available for
download on [Download the Windows Driver Kit (WDK)](download-the-wdk.md).

The Windows Driver Kit (WDK) is used to develop, test, and deploy
Windows drivers. To develop drivers, use the latest public versions of
the Windows Driver Kit (WDK) and tools, available for download on
[Download the Windows Driver Kit (WDK)](download-the-wdk.md).

This topic contains information about earlier versions of the WDK, the
Enterprise WDK (EWDK), and additional downloads for support purposes. To
use these earlier versions, you must *first* install the version of
Visual Studio that is appropriate for your targeted platform.

## Step 1: Install Visual Studio

Development of drivers is supported for specific versions of Visual
Studio. To develop a driver for a specific version of Windows, you must
use one of the versions of Visual Studio that are identified (and linked
for download) in the following table.

| Targeted versions of Windows      | Edition(s) of Visual Studio            |
|--------------------------|----------------------------------------|
| Windows 10, version 1809 <br/>Windows 10, version 1803 <br/>Windows 10, version 1709 | [Visual Studio Community 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15) <br/>[Visual Studio Professional 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15) <br/>[Visual Studio Enterprise 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15) |
| Windows 10, version 1703 <br/>Windows 10, version 1607 | [Visual Studio Express 2015 for Desktop](https://go.microsoft.com/fwlink/?linkid=875331) <br/>[Visual Studio Community 2015](https://go.microsoft.com/fwlink/p/?LinkId=534599) <br/>[Visual Studio Professional 2015](https://go.microsoft.com/fwlink/p/?LinkId=619628) <br/>[Visual Studio Enterprise 2015](https://go.microsoft.com/fwlink/p/?LinkId=619629) |
| Windows 8.1 Update <br/>Windows 8.1 | [Visual Studio 2013](https://go.microsoft.com/fwlink/?linkid=875331) |
| Windows 8                | [Visual Studio Professional 2012](https://go.microsoft.com/fwlink/p/?LinkID=255976) <br/>[Visual Studio Ultimate 2012](https://go.microsoft.com/fwlink/p/?LinkID=255982) |

### Configure Visual Studio for Windows 10, versions 1709, 1803, and 1809

When you install Visual Studio, select the **Desktop development with
C++** workload. The Windows 10 Software Development Kit (SDK) is
automatically included and is displayed in the right-hand **Summary**
pane.

To develop drivers for ARM/ARM64, choose **Individual components** and
under **Compilers, build tools, and runtimes** select **Visual C++
compilers and libraries for ARM/ARM64**.

### Install the Windows SDK to target Windows 10, versions 1607 and 1703

If your development targets systems that run Windows 10, version 1607 or Windows 10, version 1703, you should install Visual Studio 2015, and then also download and install the version of the Windows SDK for the targeted version of Windows 10, as identified in the following table.

| Targeted versions of Windows      | Version of Windows SDK            |
|--------------------------|----------------------------------------|
| Windows 10, version 1703 | [Windows SDK for Windows 10.0.15063.468](https://go.microsoft.com/fwlink/p/?LinkID=845298) |
| Windows 10, version 1607 | [Windows SDK for Windows 10.0.14393.795](https://go.microsoft.com/fwlink/p/?LinkId=838916) |
| Windows 8.1              | [Windows SDK for Windows 8.1](https://go.microsoft.com/fwlink/p/?LinkId=323507) |
| Windows 8                | [Windows SDK for Windows 8](https://go.microsoft.com/fwlink/p/?LinkId=226658) |

The Windows SDK was not included in Visual Studio 2015, so you must install the SDK separately. Later versions of Visual Studio include the Windows SDK.

## Step 2: Install the WDK

The WDK is integrated with Visual Studio and Debugging Tools for Windows
(WinDbg). This integrated environment gives you the tools you need to
develop, build, package, deploy, test, and debug drivers.

> [!Note]
> Starting with Windows 10, version 1709, installing the WDK
> will by default install the WDK extensions for Visual Studio. These
> extensions are required for integration of the WDK with Visual Studio.

| Versions of Windows      | WDK and related downloads                       |
|--------------------------|-------------------------------------------------|
| Windows 10, version 1809 | [WDK for Windows 10, version 1809](https://go.microsoft.com/fwlink/?linkid=2026156) |
| Windows 10, version 1803 | [WDK for Windows 10, version 1803](https://go.microsoft.com/fwlink/?linkid=873060) |
| Windows 10, version 1709 | [WDK for Windows 10, version 1709](https://go.microsoft.com/fwlink/p/?linkid=859232) |
| Windows 10, version 1703 | [WDK for Windows 10, version 1703](https://go.microsoft.com/fwlink/p/?LinkID=845980) |
| Windows 10, version 1607 | [WDK for Windows 10, version 1607](https://go.microsoft.com/fwlink/p/?LinkId=526733)                |
| Windows 8.1 Update       | [WDK 8.1 Update](https://go.microsoft.com/fwlink/p/?LinkId=393659) (English only) <br/>[WDK 8.1 Update Test Pack](https://go.microsoft.com/fwlink/p/?LinkID=393660) (English only) <br/>[WDK 8.1 Samples](https://go.microsoft.com/fwlink/p/?LinkId=618052) |
| Windows 8                | [WDK 8](https://go.microsoft.com/fwlink/p/?LinkID=324284) (English only) <br/>[WDK 8 redistributable components](https://go.microsoft.com/fwlink/p/?LinkID=253170) (English only) <br/>[WDK 8 Samples](https://go.microsoft.com/fwlink/p/?LinkId=616509) |
| Windows XP <br/>Windows Server 2003 | [WDK 7.1.0](https://www.microsoft.com/download/confirmation.aspx?id=11800) |


> [!IMPORTANT]
> If you have installed the WDK for Windows 10, version 1703 on a system that had the WDK for Windows 10, version 1607 installed, some files from the earlier version of the WDK might have been removed. To restore these files:
> 1. On the Start menu, enter **Apps & features** in the search box, and select **Apps & features** from the results.
> 2. Find **Windows Driver Kit - Windows 10.0.15063.0** in the list of **Apps & Features**, and then select the program.
> 3. Select **Modify**, select **Repair**, and then follow the directions on the screen.
> 4. The files will be restored.

## Optional: Install the EWDK

The Enterprise WDK (EWDK) is a standalone, self-contained, command-line environment for
building drivers and basic Win32 test applications. It includes the
Visual Studio Build Tools, the SDK, and the WDK. This environment
doesn't include all the features available in Visual Studio, such as
the integrated development environment (IDE).

Using the EWDK requires .NET Framework 4.6.1. For more information about which systems run this version of the framework, see [.NET Framework system requirements](https://docs.microsoft.com/dotnet/framework/get-started/system-requirements). For links to download the .NET Framework, see [Install the .NET Framework for developers](https://docs.microsoft.com/dotnet/framework/install/guide-for-developers).

For more information about the EWDK, see
[Using the Enterprise WDK 10](https://docs.microsoft.com/windows-hardware/drivers/develop/using-the-enterprise-wdk).

| Versions of Windows               | EWDK                              |
|-----------------------------------|-----------------------------------|
| Windows 10, version 1809          | [EWDK for Windows 10, version 1809](https://docs.microsoft.com/legal/windows/hardware/enterprise-wdk-license-2017) |
| Windows 10, version 1803          | [EWDK for Windows 10, version 1803](https://docs.microsoft.com/legal/windows/hardware/enterprise-wdk-license-2017) |
| Windows 10, version 1709          | [EWDK for Visual Studio with Build Tools 15.6](https://docs.microsoft.com/legal/windows/hardware/enterprise-wdk-license-2017) (Recommended) <br/>[EWDK for Visual Studio with Build Tools 15.4](https://docs.microsoft.com/legal/windows/hardware/enterprise-wdk-license-2017) <br/>[EWDK for Visual Studio with Build Tools 15.2](https://docs.microsoft.com/legal/windows/hardware/enterprise-wdk-license-2017) |
| Windows 10, version 1703          | [EWDK for Windows 10, version 1703](https://docs.microsoft.com/legal/windows/hardware/enterprise-wdk-license-2015) |

> [!Note]
> Starting in Windows 10 version 1709, the EWDK is ISO-based. To get started, download and mount the ISO, and then run **LaunchBuildEnv**.

## Optional: Install updated test certificates for HAL extensions

To work with HAL Extensions, prepare your development system, running Windows 10, version 1709 or a later version of Windows 10. Also install the WDK or the EWDK, and then install the updated version of the **Windows OEM HAL Extension Test Cert 2017 (TEST ONLY)**, available for download as a ZIP file: [HAL_Extension_Test_Cert_2017.zip](https://go.microsoft.com/fwlink/?linkid=872294).

For more information about using this updated certificate, see [Update for "Windows OEM HAL Extension Test Cert 2017 (TEST ONLY)" test certificate](https://support.microsoft.com/help/4131991/update-for-windows-oem-hal-extension-test-cert-2017-test-only-test-cer) on Windows Support.

## Optional: Install WinDbg Preview

WinDbg Preview is a new version of WinDbg with more modern visuals, faster windows, a full-fledged scripting experience, built with the extensible debugger data model front and center. WinDbg Preview supports debugging every version of Windows 10.

For download links and more information about WinDbg Preview, see [Download WinDbg Preview](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools#small-windbg-preview-logo-download-windbg-preview).

## Standalone tools for debugging Windows XP and Windows Vista

If you're debugging Windows XP, Windows Server 2003, Windows Vista, or
Windows Server 2008 (or using one of these operating systems to run
Debugging Tools for Windows), you need to use the Windows 7 release of
the debugging tools. It's included in the SDK for Windows 7 and .NET
Framework 4.0.

> [!IMPORTANT]
> Newer versions of the Visual C++ 2010 Redistributable can cause
> issues when you install the SDK for Windows 7. For more information, see
> [Windows SDK Fails to Install with Return Code 5100](https://support.microsoft.com/help/2717426/windows-sdk-fails-to-install-with-return-code-5100) on Microsoft Support.

Get the standalone debugging tools for Windows XP by first downloading
the Windows 7 SDK:
[Microsoft Windows SDK for Windows 7 and .NET Framework 4](https://www.microsoft.com/download/confirmation.aspx?id=8279).

To install the Debugging Tools for Windows as a standalone component,
start the SDK installer, and in the installation wizard, select
**Debugging Tools for Windows**, and clear all other components.

### Related downloads
* [Download the Windows Assessment and Deployment Kit (Windows ADK)](https://docs.microsoft.com/windows-hardware/get-started/adk-install)
* [Download the Windows HLK, HCK, or Logo Kit](https://docs.microsoft.com/windows-hardware/test/hlk/windows-hardware-lab-kit)
* [Download the debugging Tools for Windows (WinDbg)](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)
* [Download Windows Symbol Packages](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-symbols)
* [Download the WDK Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewWDK)
