# VHLT for macOS

Builds VHLT for macOS (Intel and Apple Silicon).

## Downloads

[Releases](https://github.com/BryanHaley/VHLT-macOS/releases)

## Building

For Intel Macs:
```
make TARGET=intelmac
```

For Apple Silicon Macs:
```
make TARGET=applesilicon
```

For universal binaries:
```
make universal
```

## Usage

```
TOOL        : Universal Binary
TOOL_x64    : Binary targeting Intel macOS 10.9+
TOOL_arm64  : Binary targeting Apple Silicon macOS 11.0+
```

Add these to your level editor of choice the same way you would on Windows.

**NOTE**: On Apple Silicon, I recommend using the explicit ```TOOL_arm64``` binaries. If your level editor is running in Intel mode, it may choose to run the universal binaries in Rosetta, which will result in slower compilation speeds.

## Original readme.txt

```
---- How to install ----

1. Open Hammer or Batch Compiler's configuration dialog.
  Set CSG, BSP, VIS, RAD tool pathes to the 'hlcsg.exe', 'hlbsp.exe', 'hlvis.exe', 'hlrad.exe' in 'tools' folder.
  If you are running 64-bit Windows, use the 'hlcsg_x64.exe', 'hlbsp_x64.exe', 'hlvis_x64.exe' and 'hlrad_x64.exe'.
  The main benefit of the 64-bit version is no memory allocation failures, because the 64-bit tools have access to more than 2GB of system memory.

2. Open Hammer's configuration dialog.
  Add 'zhlt.wad' into your wad list.
  Add 'zhlt.fgd' into your fgd list.

3. You may also be interested in the these tools (which are well supported by this compiler):
- Larger grid patch for Hammer
    http://forums.svencoop.com/showthread.php?p=461330#post461330
- Floating point coordinates output patch for Hammer
    http://forums.svencoop.com/showthread.php?t=39037


---- About ----

Vluzacn's ZHLT v34 (2015/8/17)
This is Vluzacn's (email: vluzacn@163.com) 34th custom build of ZHLT 3.4 (http://zhlt.info/)
More information are available at  https://web.archive.org/web/20160311125736/http://forums.svencoop.com/showthread.php/38059-archive-custom-zhlt-by-vluzacn
```