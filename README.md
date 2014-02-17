================================================================================

BDIFF / BPATCH README

================================================================================

This read-me file accompanies the binary download of the BDiff/BPatch utilities.

Contents:

1) About The Software
2) Installation
3) Source Code
4) Copyright and License
5) Change Log

--------------------------------------------------------------------------------
About The Software
--------------------------------------------------------------------------------

BDiff.exe computes differences between two binary files. Output can be either a
somewhat human-readable protocol in plain text, or a binary file that is
readable by BPatch.exe.

BPatch.exe applies a binary patch generated by BDiff.exe to a file to recreate
another file.

See the files BDiff.txt and BPatch.txt for details of how to use the programs.

BDiff.exe and BPatch.exe are derived from Stefan Reuther's bdiff and bpatch v0.2
and a later bug fix.

The original C source was translated into Object Pascal by Peter D Johnson and
the programs provided are based on updates of this code base.

The programs should run on any 32 bit version of Windows.

--------------------------------------------------------------------------------
Installation
--------------------------------------------------------------------------------

Copy the provided executable files to the required location. No further
installation is required.

You may want to modify the Windows PATH environment variable to include the
location of the programs.

To uninstall simply delete the programs. They make no changes to the system. If
you changed the PATH environment variable you may wish to adjust this.

--------------------------------------------------------------------------------
Source Code
--------------------------------------------------------------------------------

Pascal Source
-------------

The source code is maintained in a Subversion repository on assembla.com. You
can view the repository online using Assembla's code browser at
http://code.assembla.com/bdiff/subversion/nodes. The current development tree is
stored in "trunk" while snapshots of releases from v0.2.5 are provided in the
"tags" branch.

Subversion users should use the following URL in their Subversion client:
http://subversion.assembla.com/svn/bdiff. You will usually want to access the
development branch at http://subversion.assembla.com/svn/bdiff/trunk.

The source code for each branch can be downloaded by selecting the required
branch in the Assembla code browser and clicking the "Download" button.

For information on how to build the source, see Build.txt in the repository.

C Source
--------

The original C source code can be downloaded from
http://phost.de/~stefan/Files/bdiff-02.zip.

The copy used for the original Pascal translation is included in the Subversion
repository.

--------------------------------------------------------------------------------
Copyright and License
--------------------------------------------------------------------------------

See the file LICENSE for details of copyright and the license that applies to
this software. The license can also be found at
http://www.delphidabbler.com/software/bdiff/license.

The original C source is provided under different licensing terms. For details
see the comments in the ADMINISTRATIVIA section of bdiff.1 and bpatch.1 that are
located with the C source code in the Subversion repository.

--------------------------------------------------------------------------------
Change Log
--------------------------------------------------------------------------------

The change log is provided in the file ChangeLog.txt.

--------------------------------------------------------------------------------
$Rev$
$Date$