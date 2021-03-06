# ------------------------------------------------------------------------------
# Makefile for the whole project.
#
# Usage:
#   Run one of the following commands on the same directory as this file:
#     Make
#     Make everything
#       Configures ready for building, builds executable (resource and pascal)
#       Cleans up and creates release files
#     Make config
#       Configure source directories and creates binary output directories
#     Make exe
#     Make all
#       Builds both executables: same as Make res followed by Make pascal
#     Make res
#       Builds all resources.
#     Make pascal
#     Make pas
#       Builds all pascal files. Requires resources to have been built.
#     Make clean
#     Make tidy
#       Cleans up temporary files.
#     Make deepclean
#       Remove temorary files as per clean target along with generated .cfg
#       files and Build directory and its contents.
#     Make release
#       Creates binary release file.
# ------------------------------------------------------------------------------


!include "Common.mak"

# Default is to config, create executable and create release file
everything: config exe release

# Synonyms
tidy: clean
pas: pascal
all: exe

# Build executables
exe: res pascal

# Build resources
res:
  @echo.
  @echo Build Resources
  @echo ---------------
  @cd BDiff
  $(MAKE) -f BDiff.mak res
  @cd ..\BPatch
  $(MAKE) -f BPatch.mak res
  @cd ..

# Build pascal code and link in resources
pascal:
  @echo.
  @echo Build Pascal
  @echo ------------
  @cd BDiff
  $(MAKE) -f BDiff.mak pascal
  @cd ..\BPatch
  $(MAKE) -f BPatch.mak pascal
  @cd ..

# Clean up unwanted and temporary files etc created by IDE
clean:
  @echo.
  @echo Clean Unwanted Files
  @echo --------------------
  @cd ..
  -@del /S *.~* 2>nul
  -@del /S ~* 2>nul
  -@del /S *.dsk 2>nul
  -@del /S *.local 2>nul
  -@del /S *.identcache 2>nul
  -@del /S *.tvsconfig 2>nul
  -@for /F "usebackq" %i in (`dir /S /B /A:D ..\__history`) do @rmdir /S /Q %i
  @cd Src
  @echo Done.

# Clean up temporary files, generated files and delete Build directory and its
# contents
deepclean: clean
  # remove directories created by config
  @cd ..
  @if exist Build\Exe rmdir /S /Q Build\Exe
  @if exist Build\Bin rmdir /S /Q Build\Bin
  @if exist Build\Release rmdir /S /Q Build\Release
  @if exist Build rmdir /S /Q Build
  @cd Src
  # remove .cfg files created by config
  @if exist BDiff\BDiff.cfg del BDiff\BDiff.cfg
  @if exist BPatch\BPatch.cfg del BPatch\BPatch.cfg

# Build release files (.zip)
!ifndef RELEASEFILENAME
RELEASEFILENAME = dd-bdiff
!endif
OUTFILE = Build\Release\$(RELEASEFILENAME).zip
release: clean
  @echo.
  @echo Creating Release File
  @echo ---------------------
  @cd ..
  -@if exist $(OUTFILE) del $(OUTFILE)
  # Store exe files in zip file root
  @$(ZIP) -j -9 $(OUTFILE) Build\Exe\*.exe
  # Copy license and readme files to root
  @$(ZIP) -j -9 $(OUTFILE) README.md LICENSE.md CHANGELOG.txt
  # Copy other docs to docs sub-directory
  @$(ZIP) -r -9 $(OUTFILE) Docs\BDiff.txt
  @$(ZIP) -r -9 $(OUTFILE) Docs\BPatch.txt
  # Copy test code
  @$(ZIP) -r -9 $(OUTFILE) Test
  @cd Src

# Configure source code ready for compilation
config:
  @echo.
  @echo Configuring
  @echo -----------
  @echo Creating output directories
  -@if not exist ..\Build md ..\Build
  -@if not exist ..\Build\Exe md ..\Build\Exe
  -@if not exist ..\Build\Release md ..\Build\Release
  -@if not exist ..\Build\Bin md ..\Build\Bin
  -@if not exist ..\Build\Bin\BDiff md ..\Build\Bin\BDiff
  -@if not exist ..\Build\Bin\BPatch md ..\Build\Bin\BPatch
  @echo Creating .cfg file
  @cd BDiff
  @$(MAKE) -f BDiff.mak config >nul
  @cd ..\BPatch
  @$(MAKE) -f BPatch.mak config >nul
  @cd ..
