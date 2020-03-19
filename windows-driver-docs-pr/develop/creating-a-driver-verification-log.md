---
ms.assetid: 5EB802D0-1894-4D64-ACB0-77B848B7E644
title: Creating a Driver Verification Log
description: The Windows Server 2012 Hardware Certification Program requires a Driver Verification Log (DVL) for all applicable driver submissions.
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Creating a Driver Verification Log

The Windows Server [Hardware Certification Program](https://docs.microsoft.com/windows-hardware/design/compatibility/) requires a Driver Verification Log (DVL) for all driver submissions. The DVL contains a summary of the results from the Code Analysis (CA) and Static Driver Verifier (SDV) log files. The DVL does not contain any source information. You must run the Code Analysis tool and Static Driver Verifier prior to creating a DVL for your driver.

**To create a driver verification log**

1.  Before running the Code Analysis tools, be sure that you can build and link your driver using the latest Windows Driver Kit (WDK).
2.  For the Driver Solution, make sure that you have selected a Release configuration as the Solution Configuration and x64 as the Solution Platform.
3.  Run [Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier). For information about creating the log file, see [Creating a log file for Static Driver Verifier](creating-a-log-file-for-static-driver-verifier.md) and [Using Static Driver Verifier to find defects in drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers).
4.  Run the Code Analysis tool for drivers. Address and fix any defects that are found. See [Creating a log file for the code analysis tool](creating-a-log-file-for-the-code-analysis-tool.md) and [How to run Code Analysis for Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/how-to-run-code-analysis-for-drivers). For more information about code analysis, see [Analyzing C/C++ Code Quality by Using Code Analysis](https://go.microsoft.com/fwlink/p/?linkid=226836).
5.  Create the Driver Verification Log. From the **Driver** menu, click **Create Driver Verification Log...**.
6.  Verify that both the Code Analysis Log and the Static Driver Verifier Log files are detected. Click **Create**.

The driver verification log has the file name extension .DVL.XML. The log is created in the project folder, for example, \\*myDriverProject*\\*myDriverName*.DVL.XML.

**Note**  SDV performs a clean rebuild of the driver, which removes the Code Analysis log.  As such, please be sure to run SDV before running CA.

**Note**  When you are ready to test your driver using the [Windows Hardware Lab Kit](https://docs.microsoft.com/windows-hardware/test/hlk/), you need to copy the driver verification log to the %systemdrive%\\DVL directory on the test computer. Be sure to delete the contents of the directory on the test computer before you copy the new driver verification log.

 

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


For the most up-to-date information about the Code Analysis tool, Static Driver Verifier, and the Driver Verification Log, refer to the WDK Release Notes. The Release Notes are available on the [Windows Driver Kit (WDK) download page](https://go.microsoft.com/fwlink/p/?linkid=254897).

**Important**   Timeouts, spaceouts, and other non-successful results in the DVL file are acceptable for certification submission. This will not cause the Static Tools test in HCK to fail. For HCK 2.0, the Static Tools Test only requires the presence of DVL file to show Code Analysis and SDV had been run, and does not require all rules to pass.

 

You can also create the driver verification log from a Visual Studio Command Prompt window, either by the Visual Studio Native Tools Command Prompt installed with Visual Studio or via the Enterprise Windows Driver Kit (EWDK):

```cpp
msbuild.exe <vcxprojectfile> /target:dvl /p:Configuration="Release" /P:Platform=x64
```

## <span id="related_topics"></span>Related topics


* [Creating a log file for Static Driver Verifier](creating-a-log-file-for-static-driver-verifier.md)
* [Creating a log file for the code analysis tool](creating-a-log-file-for-the-code-analysis-tool.md)
* [Hardware Certification Program](https://go.microsoft.com/fwlink/p/?linkid=227016)
* [Analyzing Driver Quality by Using Code Analysis Tools](analyzing-driver-quality-by-using-code-analysis-tools.md)
* [How to run Code Analysis for drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/how-to-run-code-analysis-for-drivers)
* [Using Static Driver Verifier to find defects in drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)
 

 






