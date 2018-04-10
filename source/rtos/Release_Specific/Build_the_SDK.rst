.. http://processors.wiki.ti.com/index.php/Processor_SDK_RTOS_Building_The_SDK 

Overview
=========

The Processor SDK comes with pre-built libraries for everything you need
to start writing an application. However, you may want to customize and
rebuild from source. Inside the SDK there is a top-level Makefile that
can be used to build some of the sub-components found within the SDK.
Prior to calling this Makefile, run the provided script/batch file to
setup your host environment variables. For components not covered by
this top-level Makefile, please see guides within the respective
component for build instructions.

The Makefile and environment setup script are found in the RTOS SDK
directory:

::

     [SDK Install Path]/processor_sdk_rtos_[soc]_[version]/

The default SDK Install Path is ``C:\ti`` for Windows and
``/home/[user]/ti`` for Linux.

The pre-requisite compilers are provided in Code Compose Studio, see the
`CCS installation section of the Getting Started
Guide <http://processors.wiki.ti.com/index.php/Processor_SDK_RTOS_Getting_Started_Guide#Code_Composer_Studio>`__.

.. note::
   If you have installed the SDK and/or CCS in non-default locations follow
   the steps outlined in the article
   `Processor SDK RTOS Install In Custom Path <How_to_Guides.html#update-environment-when-installing-to-a-custom-path>`
   to build the SDK from the toplevel Makefile.

| 

.. _Build-The-SDK-Setup-Environment-label:
Setup Environment
====================

Command
---------
The SDK build environment can be configured on Windows and Linux by
running an environment setup script located in the top-level RTOS SDK
folder.

Windows
^^^^^^^^^
From the RTOS SDK directory, enter

::

     C:\ti\processor_sdk_rtos_[soc]_[version]> setupenv.bat

which will configure the Windows command shell environment for the
installed RTOS SDK.

.. note::

   -  You must re-run this batch file any time you open a new terminal.
   -  Script also sets CCS installation path using TOOLS_INSTALL_PATH
      variable so set the variable if you are not using default CCS install
      path

::

     C:\ti\processor_sdk_rtos_[soc]_[version]>setupenv.bat
     Optional parameter not configured : CG_XML_BIN_INSTALL_PATH
     REQUIRED for xdc release build
     Example: set CG_XML_BIN_INSTALL_PATH=C:/ti/cg_xml/bin
     Optional parameter not configured : DOXYGEN_INSTALL_PATH
     REQUIRED for xdc release build
     Example: set DOXYGEN_INSTALL_PATH=C:/ti/Doxygen/doxygen/1.5.1-p1/bin
     **************************************************************************
     Environment Configuration:
         PDK Directory             : /ti/PDK_AM~3/packages/
         CGTOOL INSTALL Directory  : C:/ti/ccsv6/tools/compiler/ti-cgt-c6000_[version]
         TOOLCHAIN A15 Directory   : C:/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]
         TOOLCHAIN A8 Directory    : C:/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]
         TOOLCHAIN A9 Directory    : C:/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]
         TOOLCHAIN M4 Directory    : C:/ti/ccsv6/tools/compiler/ti-cgt-arm_[version]
         FPULIB_PATH               : C:/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]/lib/gcc/arm-none-eabi/[version]/fpu
         CROSS_TOOL_PRFX           : arm-none-eabi-
         XDC_INSTALL_PATH          : C:/ti/xdctools_[version]_core
         BIOS_INSTALL_PATH         : C:/ti/bios_[version]
         IPC_INSTALL_PATH          : C:/ti/ipc_[version]
         EDMA3LLD_BIOS6_INSTALLDIR : C:/ti/edma3_lld_[version]
         NDK_INSTALL_PATH          : C:/ti/ndk_[version]
         IMGLIB_INSTALL_PATH       : C:/ti/imglib_c66x_[version]
         UIA_INSTALL_PATH          : C:/ti/uia_[version]
         PROC_SDK_INSTALL_PATH     : C:/ti/processor_sdk_rtos_[soc]_[version]
     **************************************************************************
     Changing to short name to support directory names containing spaces
     current directory: C:/ti/processor_sdk_rtos_[soc]_[version]
     PROCESSOR SDK BUILD ENVIRONMENT CONFIGURED
     **************************************************************************

.. note::
   The warnings of optional parameters not configured can be ignored since
   we are only rebuilding the libraries and not generating a release
   package.

Linux
^^^^^^^^
From the RTOS SDK directory, enter

::

     ~/ti/processor_sdk_rtos_[soc]_[version]$ source setupenv.sh

which will configure the Linux shell environment for the installed RTOS
SDK.

::

     ~/ti/processor_sdk_rtos_[soc>]_[version]$ source setupenv.sh
     Optional parameter not configured : CG_XML_BIN_INSTALL_PATH
     REQUIRED for xdc release build
     Example: export CG_XML_BIN_INSTALL_PATH="~/ti/cg_xml/bin"
     Optional parameter not configured : DOXYGEN_INSTALL_PATH
     REQUIRED for xdc release build
     Example: export DOXYGEN_INSTALL_PATH="~/ti/Doxygen/doxygen/1.5.1-p1/bin"
     **************************************************************************
     Environment Configuration:
         PDK Directory             : /home/[user]/ti/pdk_[soc]_[version]/packages
         CGTOOL INSTALL Directory  : /home/[user]/ti/ccsv6/tools/compiler/ti-cgt-c6000_[version]
         TOOLCHAIN A15 Directory   : /home/[user]/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]
         TOOLCHAIN A8 Directory    : /home/[user]/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]
         TOOLCHAIN A9 Directory    : /home/[user]/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]
         TOOLCHAIN M4 Directory    : /home/[user]/ti/ccsv6/tools/compiler/ti-cgt-arm_[version]
         FPULIB_PATH               : /home/[user]/ti/ccsv6/tools/compiler/gcc-arm-none-eabi-[version]/lib/gcc/arm-none-eabi/[version]/fpu
         CROSS_TOOL_PRFX           : arm-none-eabi-
         XDC_INSTALL_PATH          : /home/[user]/ti/xdctools_[version]_core
         BIOS_INSTALL_PATH         : /home/[user]/ti/bios_[version]
         IPC_INSTALL_PATH          : /home/[user]/ti/ipc_[version]
         EDMA3LLD_BIOS6_INSTALLDIR : /home/[user]/ti/edma3_lld_[version]
         NDK_INSTALL_PATH          : /home/[user]/ti/ndk_[version]
         IMGLIB_INSTALL_PATH       : /home/[user]/ti/imglib_c66x_[version]
         UIA_INSTALL_PATH          : /home/[user]/ti/uia_[version]
         PROC_SDK_INSTALL_PATH     : /home/[user]/ti/processor_sdk_rtos_[soc]_[version]
     
     PROCESSOR SDK BUILD ENVIRONMENT CONFIGURED
     *******************************************************************************

.. note::
   The warnings of optional parameters not configured can be ignored since
   we are only rebuilding the libraries and not generating a release
   package.


Top-Level Makefile
====================
The SDK level makefile can be used to compile SDK sub-components after
the build environment has been configured. The following sections cover
the Makefile found in the top-level of the Processor SDK for RTOS.

Target Types
--------------
For each of the targets discussed below the following target type are
defined:

-  **<target>** - This is the build target which will compile the
   release version of the component

-  **<target>_clean** - This target will clean the component

Top-Level Targets
------------------
The Processor SDK for RTOS provides the following targets by default
which will invoke the corresponding component targets:

-  **help** - This will print target information defined in the Makefile

-  **all** - This will call the build target for each component defined
   in the Makefile

-  **clean** - This will call the clean target for each component
   defined in the Makefile

.. note::
   Invoking build using "all" option in SDK top level for multicore SOC
   parts can take up to several hours to rebuild as the components need to
   be built for all cores (e.g., A15, C66x, M4). Please rebuild individual
   components in the PDK package for these devices to avoid long build times.

Common Targets
---------------
The following targets are common to all Processor SDKs for RTOS:

-  **pdk** - Builds the Platform Development Kit that includes CSL and
   low level drivers

Additional Targets
-------------------
You can find the list of all the targets by invoking **help** target as
described above. Depending on the capabilities and software available
for a given device additional targets may also be defined:

-  **demo** - Builds demonstrations provided in the SDK
-  **ipc_bios** - Builds the IPC component provided in the SDK
-  **ipc_examples** - Builds the IPC examples provided in the IPC
   component

| 

Usage Examples
================
The following examples demonstrate how to use the top-level Makefile for
some common tasks. All of the examples below assume that you are calling
the Makefile from the top-level of the SDK.

Windows
--------

-  Build all

::

     C:\ti\processor_sdk_rtos_[soc]_[version]> gmake

-  Clean all

::

     C:\ti\processor_sdk_rtos_[soc]_[version]> gmake clean

Linux
------

-  Build all

::

     ~/ti/processor_sdk_rtos_[soc]_[version]$ make

-  Clean all

::

     ~/ti/processor_sdk_rtos_[soc]_[version]$ make clean

| 

Rebuilding Components
=======================
Instructions for rebuilding sub-components can be found in documentation
within the component. Here are a collection of useful pages:

-  `Rebuild
   IPC <http://processors.wiki.ti.com/index.php/IPC_Users_Guide/Rebuilding_IPC>`__
   *(Starting in Release 3.0, IPC build has been integrated into the
   top-level SDK Makefile.)*

-  `Rebuild
   NDK <http://processors.wiki.ti.com/index.php/Rebuilding_The_NDK_Core_Using_Gmake>`__

-  `Rebuild PDK <http://processors.wiki.ti.com/index.php/Rebuilding_The_PDK>`__

-  `Rebuild
   SYS/BIOS <http://processors.wiki.ti.com/index.php/SYS/BIOS_FAQs>`__

| 

.. raw:: html

