---
title: Partner Center FAQ
description: This article provides answers to frequently asked questions about the Partner Center.
ms.assetid: AA3D1147-7015-4D21-84A6-D127F57DDC97
ms.topic: article
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Hardware dashboard FAQ

This article provides answers to frequently asked questions about the Partner Center.

## How do I contact Partner Center Support?

If you are having problems accessing the Dashboard or need Dashboard Support please open a support ticket here: https://developer.microsoft.com/windows/support.  

You must Sign-in using your Partner Center Hardware dashboard username and password for any account or submission specific questions.

Select **Contact us**,  **Dashboard issue**, and then **Hardware submissions & signing (all OS version)** from the dropdown.  Live Chat and Email support hours are 8am-8pm CST Monday-Friday.  SLA for an initial response is 24-48 hours for email support.

## Can I associate multiple certificates with a dashboard account?

One organization can associate multiple certificates with its dashboard account. Your submissions must be signed with any one of those certificates.

There is no restriction on the number of certificates (both EV and Standard) associated with your organization.

## What agreements need to be signed?

The following agreements can be signed as part of the registration process.

> [!NOTE]
> Signing the Windows Compatibility Program and Driver Quality Attestment Testing Agreement is a requirement for all registrations. All other agreements are optional unless you are using features or assets in the other associated agreements. 

* Windows Compatibility Program and Driver Quality Attestment Testing Agreement (ver 2.0)

* Windows Logo License Agreement (ver 2018)

* UEFI (Unified Extensible Firmware Interface) Firmware Agreement (ver 1.0)

* Windows Analytics Agreement (ver 2.0)

* Microsoft Collaborate Program Agreement (ver 1.0)

* Windows Desktop Applications Program Agreement (ver 1.0)

## How do I add additional users or grant additional roles to users in my company?

See [Managing User Roles](managing-user-roles.md) for more information.

## Managing submissions

### What is the hardware certification submission processing time?

All hardware submissions to the dashboard will be processed within five business days or less, depending on whether the submission requires manual review. Manual review may be required if your submission's tests fail, if it does not have a valid filter applied, or due to internal business policy.

### Why do I see a difference in download signed files?

In order to make Windows 10 more secure without affecting performance, all binaries are now receiving embedded signatures. This applies to all submissions for certification, not only Windows 10 submissions.

### How to get a single cat file if drivers are uniform for all operating systems

Make sure your final package has a single driver folder on the **Package** tab and the driver’s properties include all the operating systems you have tested. For more information, see [Walkthrough: How to get a driver signed by Microsoft for multiple versions of Windows](get-drivers-signed-by-microsoft-for-multiple-windows-versions.md).

### I'm unable to add new marketing names to the approved submission

Check the announcement date that has been set. If the announcement date has passed, you won't be able to add a new name.

### How can I share a link to a Windows Certification Verification Report?

* A sharable URL contains three identification numbers separated by slashes as shown below: `https://developer.microsoft.com/dashboard/hardware/driver/DownloadCertificationReport/SellerID/PrivateProductID/SubmissionID`

* The identification numbers used in the URL, and their locations are as follows:

| Component | Description |
| ---       | ---         |
|SellerID   | The identification number of your partner account. This can be found on the account management page, under **Account settings**. |
|PrivateProductID | The identification number generated with each product creation. Located on the driver details page for your product. See [Dashboard ID definitions](https://docs.microsoft.com/windows-hardware/drivers/dashboard/id-definitions) for more information. |
|SubmissionID | The idenfication number given to each submission and submission update. Located on the driver details page for your product. See [Dashboard ID definitions](https://docs.microsoft.com/windows-hardware/drivers/dashboard/id-definitions) for more information. |

* To create a sharable link, replace **SellerID**, **PrivateProductID**, and **SubmissionID** in the example URL above with the appropriate identification numbers.
* This URL allows the report to be accessed and downloaded without prior authorization or access to the Partner Center.

## Troubleshooting submission upload errors

### My driver signing submission fails with the error “There are files at the root of the cabinet” or “\#No .inf files found in driver directory/directories: XYZ”

The failure is caused by an incorrect .cab file structure. The .cab structure was created with driver files in the root folder of the .cab file instead of having them in a subfolder. See [Attestation signing a kernel driver for public release](attestation-signing-a-kernel-driver-for-public-release.md) for instructions on how to create a proper .cab file for your driver signing submission.

### "It looks like your package is corrupt or missing important information. Ensure you are using the latest version of the kit, regenerate your package, and try again. If you continue to experience the issue, contact Support."

If you continue to experience issues with your package submission, contact Support in the dashboard header.

### "File is using Zip64(4gb+file Size)"

This error is caused when the uploaded archive's filetype is .zip64 instead of .zip. This is caused by a large filesize. To fix this error, repackage the submission using the below steps.

1. Rename the current .hckx/hlkx file to .zip.
2. Extract to a folder.
3. Open the folder.
4. Select all items, then right-click and select **Send to Compressed zip folder**.
5. Rename the new .zip folder as .hckx/.hlkx.
6. Upload the new .hckx/.hlkx file.

### The DUA package error shows "Failed to open package" with the error “Not compatible with a version (3.2.0.0) with this instance package manager”

* Use [HLK studio](https://docs.microsoft.com/windows-hardware/test/hlk/user/install-standalone-hlk-studio) to open the downloaded DUA shell package and to create DUA submission.
