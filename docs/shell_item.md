---
tags:
  - Data Formats
---
The Windows Shell uses Shell Items (or Shell Item list) to identify items
within the Windows Folder Hierarchy. A Shell Item list is much like a "path",
and is unique to its parent folder. The format of the Shell Item is
undocumented and varies between Windows versions.

The Shell Item is used in [Windows Shortcut (lnk)](lnk.md) file and the
ShellBags key in the [Windows Registry](windows_registry.md).

## Format

The basic format is a list, consisting of a (shell item) entry size
value (field) and entry data.

There are multiple types of entries to specify different parts of the
"path":

- volume
- network share
- file and directory
- URI

Some shell item entries contain date and time values which can be used
in [Timeline Analysis](timeline_analysis.md).

### Notes

From
<https://learn.microsoft.com/en-us/windows/win32/shell/nse-implement#interpreting-pidls>

    Some methods, such as IShellFolder::GetUIObjectOf, use PIDLs that are relative to the parent folder and are straightforward to interpret.

    ...

    What complicates the task of associating an object with a fully qualified PIDL is that one or more of the initial SHITEMID structures in the PIDL might belong to objects that lie outside your extension in the Shell namespace. You have no way of interpreting the meaning of the abID member of those structures. What your extension must do is to "walk" the list of SHITEMID structures, until you reach the structure that corresponds to your root folder. From then on, you will know how to interpret the information in the SHITEMID structures.

## Example

An example of a shell item list taken from **Calculator.lnk**

    shell item type                     : 0x1f
    shell item sort order               : 0x50
    shell item folder identifier        : 20d04fe0-3aea-1069-a2d8-08002b30309d
    shell item folder name              : My Computer

    shell item type                     : 0x2f
    shell item volume name              : C:\

    shell item type                     : 0x31
    shell item file size                : 0
    shell item modification time        : Dec 31, 2010 13:28:48 UTC
    shell item file attribute flags     : 0x0010
            Is directory (FILE_ATTRIBUTE_DIRECTORY)

    shell item short name               : WINDOWS
    shell item extension size           : 38
    shell item extension version        : 3
    shell item creation time            : Dec 31, 2010 13:26:18 UTC
    shell item access time              : Dec 31, 2010 13:28:52 UTC
    shell item long name                : WINDOWS

    shell item type                     : 0x31
    shell item file size                : 0
    shell item modification time        : Dec 31, 2010 13:28:38 UTC
    shell item file attribute flags     : 0x0010
            Is directory (FILE_ATTRIBUTE_DIRECTORY)

    shell item short name               : system32
    shell item extension size           : 40
    shell item extension version        : 3
    shell item creation time            : Dec 31, 2010 13:26:18 UTC
    shell item access time              : Dec 31, 2010 13:28:38 UTC
    shell item long name                : system32

    shell item type                     : 0x32
    shell item file size                : 115712
    shell item modification time        : Mar 25, 2003 12:00:00 UTC
    shell item file attribute flags     : 0x0020
            Should be archived (FILE_ATTRIBUTE_ARCHIVE)

    shell item short name               : calc.exe
    shell item extension size           : 40
    shell item extension version        : 3
    shell item creation time            : Dec 31, 2010 13:06:06 UTC
    shell item access time              : Dec 31, 2010 13:06:06 UTC
    shell item long name                : calc.exe

## See Also

- [Jump Lists](jump_lists.md)
- [LNK](lnk.md)

## External Links

- [MSDN: Introduction to the Shell Namespace (Windows)](https://learn.microsoft.com/en-us/windows/win32/shell/namespace-intro)
- [Implementing the Basic Folder Object Interfaces](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/cc144093(v=vs.85))
- [ShellBags Registry Forensics](https://www.sans.org/digital-forensics-incident-response/),
  by johnmccash, October 2008
- [Shell Bag Format Analysis](http://42llc.net/?p=385), by Yogesh Khatri,
  October 2009 (appears to be no longer available)
- [Using shellbag information to reconstruct user activities](http://old.dfrws.org/2009/proceedings/p69-zhu.pdf),
  by Yuandong Zhu, Pavel Gladyshev, Joshua James, 2009
- [Windows Shell Item format](https://github.com/libyal/libfwsi/blob/main/documentation/Windows%20Shell%20Item%20format.asciidoc),
  by the libfwsi project, July 2010 (work in progress)
- [Computer Forensic Artifacts: Windows 7 Shellbags](https://www.sans.org/digital-forensics-incident-response/),
  Chad Tilbury, July 5, 2011
- [MoVP 3.2 Shellbags in Memory, SetRegTime, and TrueCrypt Volumes](https://volatility-labs.blogspot.com/2012/09/movp-32-shellbags-in-memory-setregtime.html),
  by Jamie Levy, September 2012
- [Shellbag Analysis, Revisited...Some Testing](http://windowsir.blogspot.com/2012/10/shellbag-analysis-revisitedsome-testing.html),
  by [Harlan Carvey](harlan_carvey.md), October 2012
- [Shellbags Forensics: Addressing a Misconception (interpretation, step-by-step testing, new findings, and more)](https://www.4n6k.com/2013/12/shellbags-forensics-addressing.html),
  by Dan Pullega, December 4, 2013 (RESTRICTED)
- [Part 5: USB Device Research – Directory Traversal Artifacts (Shell bagMRU Entries)](http://www.nicoleibrahim.com/part-5-usb-device-research-directory-traversal-artifacts-shell-bagmru-entries/),
  by Nicole Ibrahim, December 31, 2013
- [ReactOS: Shell Documentation](https://reactos.org/wiki/Shell_Documentation)
