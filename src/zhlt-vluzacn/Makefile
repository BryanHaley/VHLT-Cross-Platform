
#
# Makefile for UNIX-like environments
#
# Usage:
#   make            - Build all tools. They will be copied into 'bin' directory.
#   make clean      - Clean.
#   make hlcsg      - Build hlcsg.
#   make hlbsp      - Build hlbsp.
#   make hlvis      - Build hlvis.
#   make hlrad      - Build hlrad.
#   make ripent     - Build ripent.
#   make TARGET=foo - Build for a cross compilation target.
#   make universal  - Build universal (arm64 + x64) binaries on macOS hosts.
#
# Available cross-compilation targets: 
#   linux_x64    (Build for Linux x64 on Linux hosts).
#   linux_x86    (Build for Linux x86 on Linux hosts).
#   applesilicon (Build for ARM64 Apple Silicon macOS 11 on macOS hosts).
#   intelmac     (Build for x64 Intel macOS 11 on macOS hosts).
#
# Before running the tools, please make sure the default maximum stack size on your computer
#   is more than 4MB.
#
# When compiling with g++:
#   Flag '-fno-strict-aliasing' is a must.
#   All macro definitions should not be changed, because all code were written and checked under this assumption.
#   The following warnings should be ignored:
#     warning: no newline at end of file
#     warning: '???' may be used uninitialized in this function
#     warning: suggest parentheses around assignment used as truth value
#     warning: passing ‘float’ for argument 1 to ‘void seconds_to_hhmm(unsigned int, unsigned int&, unsigned int&, unsigned int&, unsigned int&)’
#     warning: ignoring #pragma warning
#     warning: comparison between signed and unsigned integer expressions
#     warning: enumeration value ‘???’ not handled in switch
#     warning: unused variable ‘???’
#     warning: converting to ‘int’ from ‘vec_t’
#




#
# Common .cpp and .h files for all projects
#

COMMON_CPPFILES = \
			common/blockmem.cpp \
			common/bspfile.cpp \
			common/cmdlib.cpp \
			common/cmdlinecfg.cpp \
			common/filelib.cpp \
			common/log.cpp \
			common/mathlib.cpp \
			common/messages.cpp \
			common/scriplib.cpp \
			common/threads.cpp \
			common/winding.cpp \

COMMON_INCLUDEDIRS = \
			template \
			common \

COMMON_INCLUDEFILES = \
			template/basictypes.h \
			common/blockmem.h \
			common/boundingbox.h \
			common/bspfile.h \
			common/cmdlib.h \
			common/cmdlinecfg.h \
			common/filelib.h \
			common/hlassert.h \
			common/log.h \
			common/mathlib.h \
			common/mathtypes.h \
			common/messages.h \
			common/scriplib.h \
			common/threads.h \
			common/win32fix.h \
			common/winding.h \

COMMON_DEFINITIONS = \
			VERSION_LINUX \
			SYSTEM_POSIX \
			NDEBUG \
			STDC_HEADERS \
			HAVE_FCNTL_H \
			HAVE_PTHREAD_H \
			HAVE_SYS_RESOURCE_H \
			HAVE_SYS_STAT_H \
			HAVE_SYS_TIME_H \
			HAVE_UNISTD_H \

COMMON_FLAGS = -Wall -O2 -fno-strict-aliasing -pthread -pipe

#
# Specific .cpp and .h files for hlcsg, hlbsp, hlvis, hlrad and ripent
#

HLCSG_CPPFILES = \
			$(COMMON_CPPFILES) \
			hlcsg/ansitoutf8.cpp \
			hlcsg/autowad.cpp \
			hlcsg/brush.cpp \
			hlcsg/brushunion.cpp \
			hlcsg/hullfile.cpp \
			hlcsg/map.cpp \
			hlcsg/properties.cpp \
			hlcsg/qcsg.cpp \
			hlcsg/textures.cpp \
			hlcsg/wadcfg.cpp \
			hlcsg/wadinclude.cpp \
			hlcsg/wadpath.cpp \

HLCSG_INCLUDEDIRS = \
			$(COMMON_INCLUDEDIRS) \
			hlcsg \

HLCSG_INCLUDEFILES = \
			$(COMMON_INCLUDEFILES) \
			hlcsg/csg.h \
			hlcsg/wadpath.h \

HLCSG_DEFINITIONS = \
			$(COMMON_DEFINITIONS) \
			HLCSG \
			DOUBLEVEC_T \
			
HLBSP_CPPFILES = \
			$(COMMON_CPPFILES) \
			hlbsp/brink.cpp \
			hlbsp/merge.cpp \
			hlbsp/outside.cpp \
			hlbsp/portals.cpp \
			hlbsp/qbsp.cpp \
			hlbsp/solidbsp.cpp \
			hlbsp/surfaces.cpp \
			hlbsp/tjunc.cpp \
			hlbsp/writebsp.cpp \

HLBSP_INCLUDEDIRS = \
			$(COMMON_INCLUDEDIRS) \
			hlbsp \

HLBSP_INCLUDEFILES = \
			$(COMMON_INCLUDEFILES) \
			hlbsp/bsp5.h \

HLBSP_DEFINITIONS = \
			$(COMMON_DEFINITIONS) \
			HLBSP \
			DOUBLEVEC_T \

HLVIS_CPPFILES = \
			$(COMMON_CPPFILES) \
			hlvis/flow.cpp \
			hlvis/vis.cpp \
			hlvis/zones.cpp \

HLVIS_INCLUDEDIRS = \
			$(COMMON_INCLUDEDIRS) \
			hlvis \

HLVIS_INCLUDEFILES = \
			$(COMMON_INCLUDEFILES) \
			hlvis/vis.h \
			hlvis/zones.h \

HLVIS_DEFINITIONS = \
			$(COMMON_DEFINITIONS) \
			HLVIS \

HLRAD_CPPFILES = \
			$(COMMON_CPPFILES) \
			hlrad/compress.cpp \
			hlrad/lerp.cpp \
			hlrad/lightmap.cpp \
			hlrad/loadtextures.cpp \
			hlrad/mathutil.cpp \
			hlrad/nomatrix.cpp \
			hlrad/qrad.cpp \
			hlrad/qradutil.cpp \
			hlrad/sparse.cpp \
			hlrad/trace.cpp \
			hlrad/transfers.cpp \
			hlrad/transparency.cpp \
			hlrad/vismatrix.cpp \
			hlrad/vismatrixutil.cpp \

HLRAD_INCLUDEDIRS = \
			$(COMMON_INCLUDEDIRS) \
			hlrad \

HLRAD_INCLUDEFILES = \
			$(COMMON_INCLUDEFILES) \
			common/anorms.h \
			hlrad/compress.h \
			hlrad/qrad.h \

HLRAD_DEFINITIONS = \
			$(COMMON_DEFINITIONS) \
			HLRAD \

RIPENT_CPPFILES = \
			$(COMMON_CPPFILES) \
			ripent/ripent.cpp \

RIPENT_INCLUDEDIRS = \
			$(COMMON_INCLUDEDIRS) \
			ripent \

RIPENT_INCLUDEFILES = \
			$(COMMON_INCLUDEFILES) \
			ripent/ripent.h \

RIPENT_DEFINITIONS = \
			$(COMMON_DEFINITIONS) \
			RIPENT \

#
# Commands
#

CC  := gcc
CXX := g++

COPY_FILE := cp
RM_FILE   := rm
MAKE_DIR  := mkdir -p
COPY_DIR  := cp -r
RM_DIR    := rm -rf
MAKE      := make

CREATE_UNIVERSAL := lipo -create
PRINT_HEAD := head -n 40

#
# Platform options
#

HLBSP_EXE  := hlbsp
HLCSG_EXE  := hlcsg
HLVIS_EXE  := hlvis
HLRAD_EXE  := hlrad
RIPENT_EXE := ripent

TARGET :=
PLATFORM_CFLAGS :=
PLATFORM_LFLAGS :=

ifeq ($(TARGET),linux_x64)
	PLATFORM_CFLAGS += -m64
	PLATFORM_LFLAGS += -m64
	HLBSP_EXE  := $(addsuffix _x64,$(HLBSP_EXE))
	HLCSG_EXE  := $(addsuffix _x64,$(HLCSG_EXE))
	HLVIS_EXE  := $(addsuffix _x64,$(HLVIS_EXE))
	HLRAD_EXE  := $(addsuffix _x64,$(HLRAD_EXE))
	RIPENT_EXE := $(addsuffix _x64,$(RIPENT_EXE))
else ifeq ($(TARGET),linux_x86)
	PLATFORM_CFLAGS += -m32
	PLATFORM_LFLAGS += -m32
	HLBSP_EXE  := $(addsuffix _x86,$(HLBSP_EXE))
	HLCSG_EXE  := $(addsuffix _x86,$(HLCSG_EXE))
	HLVIS_EXE  := $(addsuffix _x86,$(HLVIS_EXE))
	HLRAD_EXE  := $(addsuffix _x86,$(HLRAD_EXE))
	RIPENT_EXE := $(addsuffix _x86,$(RIPENT_EXE))
else ifeq ($(TARGET),applesilicon)
	PLATFORM_CFLAGS += -target arm64-apple-macos11
	PLATFORM_LFLAGS += -target arm64-apple-macos11
	HLBSP_EXE  := $(addsuffix _arm64,$(HLBSP_EXE))
	HLCSG_EXE  := $(addsuffix _arm64,$(HLCSG_EXE))
	HLVIS_EXE  := $(addsuffix _arm64,$(HLVIS_EXE))
	HLRAD_EXE  := $(addsuffix _arm64,$(HLRAD_EXE))
	RIPENT_EXE := $(addsuffix _arm64,$(RIPENT_EXE))
else ifeq ($(TARGET),intelmac)
	PLATFORM_CFLAGS += -target x86_64-apple-macos11
	PLATFORM_LFLAGS += -target x86_64-apple-macos11
	HLBSP_EXE  := $(addsuffix _x64,$(HLBSP_EXE))
	HLCSG_EXE  := $(addsuffix _x64,$(HLCSG_EXE))
	HLVIS_EXE  := $(addsuffix _x64,$(HLVIS_EXE))
	HLRAD_EXE  := $(addsuffix _x64,$(HLRAD_EXE))
	RIPENT_EXE := $(addsuffix _x64,$(RIPENT_EXE))
endif

#
# Build rules
#

.PHONY : all
all : bin/$(HLCSG_EXE) bin/$(HLBSP_EXE) bin/$(HLVIS_EXE) bin/$(HLRAD_EXE) bin/$(RIPENT_EXE) printusage
	@echo ======== OK ========

.PHONY : hlcsg
hlcsg : bin/$(HLCSG_EXE) printusage
	@echo ======== OK ========

.PHONY : hlbsp
hlbsp : bin/$(HLBSP_EXE) printusage
	@echo ======== OK ========

.PHONY : hlvis
hlvis : bin/$(HLVIS_EXE) printusage
	@echo ======== OK ========

.PHONY : hlrad
hlrad : bin/$(HLRAD_EXE) printusage
	@echo ======== OK ========

.PHONY : ripent
ripent : bin/$(RIPENT_EXE) printusage
	@echo ======== OK ========

bin/$(HLCSG_EXE) : $(HLCSG_CPPFILES:%.cpp=hlcsg/release/%.o) printusage
	@echo ======== hlcsg : linking ========
	$(MAKE_DIR) hlcsg/release/bin
	$(CXX) $(COMMON_FLAGS) $(PLATFORM_LFLAGS) -o hlcsg/release/bin/hlcsg $(addprefix -I,$(HLCSG_INCLUDEDIRS)) $(addprefix -D,$(HLCSG_DEFINITIONS)) $(HLCSG_CPPFILES:%.cpp=hlcsg/release/%.o)
	$(MAKE_DIR) bin
	$(COPY_FILE) hlcsg/release/bin/hlcsg bin/$(HLCSG_EXE)

$(HLCSG_CPPFILES:%.cpp=hlcsg/release/%.o) : hlcsg/release/%.o : %.cpp $(HLCSG_INCLUDEFILES) printusage
	@echo ======== hlcsg : compiling $< ========
	$(MAKE_DIR) $(dir $@)
	$(CXX) -c $(COMMON_FLAGS) $(PLATFORM_CFLAGS) -o $@ $(addprefix -I,$(HLCSG_INCLUDEDIRS)) $(addprefix -D,$(HLCSG_DEFINITIONS)) $<

bin/$(HLBSP_EXE) : $(HLBSP_CPPFILES:%.cpp=hlbsp/release/%.o) printusage
	@echo ======== hlbsp : linking ========
	$(MAKE_DIR) hlbsp/release/bin
	$(CXX) $(COMMON_FLAGS) $(PLATFORM_LFLAGS) -o hlbsp/release/bin/hlbsp $(addprefix -I,$(HLBSP_INCLUDEDIRS)) $(addprefix -D,$(HLBSP_DEFINITIONS)) $(HLBSP_CPPFILES:%.cpp=hlbsp/release/%.o)
	$(MAKE_DIR) bin
	$(COPY_FILE) hlbsp/release/bin/hlbsp bin/$(HLBSP_EXE)

$(HLBSP_CPPFILES:%.cpp=hlbsp/release/%.o) : hlbsp/release/%.o : %.cpp $(HLBSP_INCLUDEFILES) printusage
	@echo ======== hlbsp : compiling $< ========
	mkdir -p $(dir $@)
	$(CXX) -c $(COMMON_FLAGS) $(PLATFORM_CFLAGS) -o $@ $(addprefix -I,$(HLBSP_INCLUDEDIRS)) $(addprefix -D,$(HLBSP_DEFINITIONS)) $<

bin/$(HLVIS_EXE) : $(HLVIS_CPPFILES:%.cpp=hlvis/release/%.o) printusage
	@echo ======== hlvis : linking ========
	$(MAKE_DIR) hlvis/release/bin
	$(CXX) $(COMMON_FLAGS) $(PLATFORM_LFLAGS) -o hlvis/release/bin/hlvis $(addprefix -I,$(HLVIS_INCLUDEDIRS)) $(addprefix -D,$(HLVIS_DEFINITIONS)) $(HLVIS_CPPFILES:%.cpp=hlvis/release/%.o)
	$(MAKE_DIR) bin
	$(COPY_FILE) hlvis/release/bin/hlvis bin/$(HLVIS_EXE)

$(HLVIS_CPPFILES:%.cpp=hlvis/release/%.o) : hlvis/release/%.o : %.cpp $(HLVIS_INCLUDEFILES) printusage
	@echo ======== hlvis : compiling $< ========
	$(MAKE_DIR) $(dir $@)
	$(CXX) -c $(COMMON_FLAGS) $(PLATFORM_CFLAGS) -o $@ $(addprefix -I,$(HLVIS_INCLUDEDIRS)) $(addprefix -D,$(HLVIS_DEFINITIONS)) $<

bin/$(HLRAD_EXE) : $(HLRAD_CPPFILES:%.cpp=hlrad/release/%.o) printusage
	@echo ======== hlrad : linking ========
	$(MAKE_DIR) hlrad/release/bin
	$(CXX) $(COMMON_FLAGS) $(PLATFORM_LFLAGS) -o hlrad/release/bin/hlrad $(addprefix -I,$(HLRAD_INCLUDEDIRS)) $(addprefix -D,$(HLRAD_DEFINITIONS)) $(HLRAD_CPPFILES:%.cpp=hlrad/release/%.o)
	$(MAKE_DIR) bin
	$(COPY_FILE) hlrad/release/bin/hlrad bin/$(HLRAD_EXE)

$(HLRAD_CPPFILES:%.cpp=hlrad/release/%.o) : hlrad/release/%.o : %.cpp $(HLRAD_INCLUDEFILES) printusage
	@echo ======== hlrad : compiling $< ========
	$(MAKE_DIR) $(dir $@)
	$(CXX) -c $(COMMON_FLAGS) $(PLATFORM_CFLAGS) -o $@ $(addprefix -I,$(HLRAD_INCLUDEDIRS)) $(addprefix -D,$(HLRAD_DEFINITIONS)) $<

bin/$(RIPENT_EXE) : $(RIPENT_CPPFILES:%.cpp=ripent/release/%.o) printusage
	@echo ======== ripent : linking ========
	$(MAKE_DIR) ripent/release/bin
	$(CXX) $(COMMON_FLAGS) $(PLATFORM_LFLAGS) -o ripent/release/bin/ripent $(addprefix -I,$(RIPENT_INCLUDEDIRS)) $(addprefix -D,$(RIPENT_DEFINITIONS)) $(RIPENT_CPPFILES:%.cpp=ripent/release/%.o)
	$(MAKE_DIR) bin
	$(COPY_FILE) ripent/release/bin/ripent bin/$(RIPENT_EXE)

$(RIPENT_CPPFILES:%.cpp=ripent/release/%.o) : ripent/release/%.o : %.cpp $(RIPENT_INCLUDEFILES) printusage
	@echo ======== ripent : compiling $< ========
	$(MAKE_DIR) $(dir $@)
	$(CXX) -c $(COMMON_FLAGS) $(PLATFORM_CFLAGS) -o $@ $(addprefix -I,$(RIPENT_INCLUDEDIRS)) $(addprefix -D,$(RIPENT_DEFINITIONS)) $<

.PHONY : printusage
printusage :
	@$(PRINT_HEAD) Makefile

.PHONY : universal
universal :
	@echo ======== compiling arm64 tools ========
	$(MAKE) TARGET=applesilicon
	@echo ======== compiling x64 tools ========
	$(MAKE) TARGET=intelmac
	@echo ======== creating universal binaries ========
	$(CREATE_UNIVERSAL) -output bin/hlcsg bin/hlcsg_x64 bin/hlcsg_arm64
	$(CREATE_UNIVERSAL) -output bin/hlbsp bin/hlbsp_x64 bin/hlbsp_arm64
	$(CREATE_UNIVERSAL) -output bin/hlvis bin/hlvis_x64 bin/hlvis_arm64
	$(CREATE_UNIVERSAL) -output bin/hlrad bin/hlrad_x64 bin/hlrad_arm64
	$(CREATE_UNIVERSAL) -output bin/ripent bin/ripent_x64 bin/ripent_arm64
	@echo ======== OK ========

#
# Clean
#

.PHONY : clean
clean : printusage
	-$(RM_DIR) hlcsg/release
	-$(RM_DIR) hlbsp/release
	-$(RM_DIR) hlvis/release
	-$(RM_DIR) hlrad/release
	-$(RM_DIR) ripent/release
	-$(RM_DIR) bin
	@echo ======== OK ========


