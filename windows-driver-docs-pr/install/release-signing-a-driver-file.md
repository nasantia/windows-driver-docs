---
title: Release-Signing a Driver File
description: Release-Signing a Driver File
ms.assetid: 3da0377d-57cf-4bd4-b3ce-6ba4ebbc3ceb
keywords:
- public release driver signing WDK , driver files
- driver file release signing WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Release-Signing a Driver File


Use the following **SignTool** for 64-bit versions of Windows Vista and later versions of Windows must have an embedded SPC signature.

```cpp
SignTool sign /v /ac CrossCertificateFile /s SPCCertificateStore /n SPCCertificateName /t http://timestamp.digicert.com DriverFileName.sys
```

Where:

-   The **sign** command configures SignTool to embed a signature in the file *DriverFileName.sys*.

-   The **/v** verbose option configures SignTool to print execution and warning messages.

-   The **/ac** *CrossCertificateFile* option specifies the cross-certificate *.cer* file that is associated with the SPC that is specified by *SPCCertificateName*.

-   The **/s** *SPCCertificateStore* option specifies the name of the Personal certificate store that holds the SPC that is specified by *SPCCertificateName*. As described in [Software Publisher Certificate (SPC)](software-publisher-certificate.md), the certificate information must be contained in a *.pfx* file, and the information in the *.pfx* file must be added to the Personal certificate store of the local computer. The Personal certificate store is specified by the option **/s my**.

-   The **/n** *SPCCertificateName* option specifies the name of the certificate in the *SPCCertificateStore* certificate store.

-   The **/t** *http://timestamp.digicert.com option supplies the URL to the publicly-available time-stamp server that DigiCert provides.

-   *DriverFileName.sys* is the name of the driver file.

The following command embeds a signature in *Toaster.sys* that is generated from a certificate named "contoso.com" in the Personal "my" certificate store and the corresponding cross-certificate *Rsacertsvrcross.cer*. In addition, the signature is time-stamped by the time stamp service http://timestamp.digicert.com. In this example, *Toaster.sys* is in the *amd64* subdirectory under the directory in which the command is run.

```cpp
SignTool sign /v /ac c:\lab\rsacertsrvcross.cer /s my /n contoso.com /t http://timestamp.digicert.com amd64\toaster.sys
```

 

 





