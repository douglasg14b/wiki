---
tags:
  - Live CD
  - Open Source Software
  - Tools
  - Windows
---

**Windows Forensic Environment** - a forensically sound bootable CD/USB
to acquire electronic media or conduct forensic analysis.

## Windows Forensic Environment ("WinFE")

WinFE was developed and researched in 2008 by Troy Larson, Sr Forensic
Examiner and Research at Microsoft
[1](http://www.twine.com/item/113421dk0-g99/windows-fe). WinFE is based
off the Windows Pre-installation Environment of media being Read Only by
default. It works similar to Linux forensic CDs that are configured not
to mount media upon booting. However, unlike Linux boot CDs, with Win FE
one can use Windows based software. Thus it is possible to include
various forensic software and general portable utilities. WinFE can also
be configured to boot from a USB device, should the evidence computer
have the ability to boot to USB.

WinFE can be customized to the examiner's needs through batch files
using the Windows Automated Install Kit (WAIK) or through 3rd party
utilities such as WinBuilder [2](http://reboot.pro).

Some examples of Windows based forensic utilities that can run in the
Windows Forensic Environment include:

- X-Ways Forensics [3](https://www.x-ways.net/),
- AccessData FTK Imager [4](https://www.exterro.com),
- Guidance Software Encase [5](https://www.opentext.com/products/security-cloud),
- ProDiscover [6](http://www.techpathways.net),
- RegRipper [7](https://regripper.wordpress.com/).

A write protection tool developed by Colin Ramsden was released in 2012
that provides a GUI for disk toggling [8](http://www.ramsdens.org.uk/).
Colin Ramsden's write protect tool effectively replaces the command line
to toggle disks on/offline or readonly/readwrite.

## Technical Background and Forensic Soundness

Windows FE is based on the modification of just two entries in the
Windows Registry. The first key is located at
"HKEY_LOCAL_MACHINE\system\ControlSet001\Services\MountMgr". The DWord
"NoAutoMount" has to be set to "1". By doing this the Mount-Manager
service will not automatically mount any storage device. The second key
is "HKEY_LOCAL_MACHINE\system\ControlSet001\Services\partmgr\Parameters"
where "SanPolicy" has to be set to "3". While both keys will avoid the
mounting of storage devices the user has to mount the storage drive
manually by using the command-line tool DiskPart, while the evidence
drive does not need to be mounted for imaging/forensic access.

The latest modification (New for Windows 8) to the registry is SAN
policy 4. SAN policy 4 Makes internal disks offline. Note. All external
disks and the boot disk are online.

Testing has shown that mounting a **volume** in READ ONLY mode will
write a controlling code to the disk, whereas mounting a **disk** in
READ ONLY mode will not make any changes. Depending on the type of
filesystem there is a potential modification to the disk with a
documented 4-byte change to non-user created data. This modification
exists for non-Windows OS disks, where Windows (FE) will write a Windows
drive signature to the disk, although it is not shown to be consistent.
Various issues with Linux Boot CDs can be compared
[9](forensic_live_cd_issues.md) ).

## Resources:

* [Windows Forensic Environment blog](https://winfe.wordpress.com/)
* [Article on Win FE in Hakin9 magazine 2009-06](https://hakin9.org/)
* [WinPE Technical Reference](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/winpe-intro?view=windows-11)
* [Windows Automated Installation Kit](https://www.microsoft.com/en-us/download/details.aspx?id=5753)
* [WinFE Write Protect tool](http://www.ramsdens.org.uk/)
