# PDC20230
Promise PDC20230 IDE Device Driver



                            README File
                            ===========

       On this diskette you will find device drivers for the
       VL-Bus IDE Disk Controller.

       VLIDE.EXE    (Version 1.10) is the installation utility.
       VLIDE.SYS    (Version 2.2a) is the driver for DOS.
       VLIDE.386    (Version 2.20) is the driver for Microsoft Windows 3.1.
       VLIDE.ADD    (Version 2.10) is the driver for IBM OS/2 2.0 and 2.1
       VLIDE310.DSK (Version 2.20) is the driver for Netware 386 3.10.
       VLIDE311.DSK (Version 2.20) is the driver for Netware 386 3.11.
       VLIDE401.DSK (Version 2.30) is the driver for Netware 386 4.01.
       VLIDE401.DDI is the installation information file for Netware 386 4.01.
       VLIDENT.SYS  (Version 2.10) is the driver for Microsoft Windows NT 3.1.
       NTINS.BAT    is the installation batch file for Windows NT 3.1.
       NTUNINS.BAT  is the removal batch file for Windows NT 3.1.
       PTIREG.EXE   is the internal utility for Windows NT 3.1.
       PTIUREG.EXE  is the internal utility for Windows NT 3.1.
       CITURBO.EXE  is the set mode utility for Windows NT 3.1.


     +========================================+
     |  DOS Driver for VL-Bus IDE Controller  |
     +========================================+


     Your VL-IDE disk controller needs the device drivers to take the
     advantage of the high performance 32-bit VL-Bus when running under
     assorted operating systems.

     The installation program "VLIDE.EXE" can install the DOS driver and
     Windows driver for you automatically. You may choose to install the
     driver manually as required. When you decide to install the driver
     manually, please follow the steps below:

     1. Copy the driver VLIDE.SYS to your system in the appropriate path.

     2. Add this following statement to your CONFIG.SYS file:

      device = [drive:][\path\] VLIDE.SYS [/P] [/F or /T] [/W] [/D0:n] [/D1:m]

        where [drive:] and [\path\] point to the directory that contains the
        the VLIDE.SYS file. The parameters F, T and W define the operating
        mode, and D0, n, D1, m define the speed settings of the attached
        hard drives.

         P   : if your IDE drive is not fully compatible with the power
               saving functions.
         F   : VL-IDE controller working in the Fast mode
         T   : VL-IDE controller working in the Turbo mode (default operating
               mode)
         W   : VL-IDE controller working in the 16-bit data access mode.
         D0  : drive 0 speed setting
         n   : drive 0 speed from 0 to 7
         D1  : drive 1 speed setting
         m   : drive 1 speed from 0 to 7

       Under Fast(F) mode, the VL-IDE disk controller supports 32-bit VL-Bus
       I/O. Under Turbo (T) mode, the VL-IDE not only supports 32-bit VL-Bus
       I/O but also read/write multiple commands. Since read/write multiple
       commands allow the host to access disk data in multiple-sector blocks,
       the Turbo mode will usually be faster.

       Note that not all IDE drives support the read/write multiple commands.
       Usually, you may set your VL-IDE to run under the Turbo mode. When
       your system is brought up, the driver VLIDE.SYS will automatically
       issue an Identify Drive command to check if the attached IDE drive(s)
       support the read/write multiple commands. In the case your drive(s)
       does not support the read/write multiple commands, the VL-IDE disk
       controller will automatically be forced to run under the Fast mode.

       Please also note: While some IDE drives may respond to the Identify
       Drive command and confirm its capability to support the read/write
       multiple commands, they may not support the read/write multiple
       commands properly. In such cases, you will need to specify the
       operating mode as "F" explicitly to ensure reliable operation of
       such IDE drives.

       Example:

       If the DOS driver VLIDE.SYS resides in the root directory of the
       drive C:. If you want your VL-IDE controller to run under TURBO mode,
       drive 0 speed 3, and drive 1 speed 5. Please add the following
       statement to the file CONFIG.SYS.

          device= c:\VLIDE.SYS /D0:3 /D1:5

       Add the following statement if your VL-IDE controller has to run
       under the Fast mode:

          device= c:\VLIDE.SYS /f

     If the DOS driver is installed manually, you might have the following
     three types of prompt messages when you boot up the system.

     (a) HDD 0 setting: FAST  Mode, Speed 5 by DEVICE DRIVER AUTOMATICALLY
         HDD 1 setting: Turbo Mode, Speed 5 by DEVICE DRIVER AUTOMATICALLY

         Where the operating mode and the speed parameter may vary with the
         hard drive(s) attached. This message will be shown when the device
         driver is installed without any user specified parameter and the
         drive(s) attached can be found in the internal table of the DOS
         device driver.

     (b) HDD 0 setting: FAST  Mode, Speed 2 by HARDWARE JUMPER SETTING
         HDD 1 setting: Turbo Mode, Speed 2 by HARDWARE JUMPER SETTING


           +--------------------------------------------------+
           |                      Notice                      |
           |   To optimize the performance of your HDD(s),    |
           |     please execute the Installation Utility      |
           |       to reconfigure your device driver          |
           +--------------------------------------------------+
                                                              +
         Where the operating mode and speed parameter may vary with the
         hard drive(s) attached. This message will be shown when the
         HDD(s) can't be found in the internal table. It might appear
         when the drive(s) are brand new model for the device driver, or
         the device driver is copied from other PC's hard drive. The
         Installation Utility stands for the VLIDE.EXE.

     (c) HDD 0 setting: FAST  Mode, Speed 5 by USER DEFINED SETTING
         HDD 1 setting: Turbo Mode, Speed 5 by USER DEFINED SETTING

           +------------------------------------------------------+
           |                      Notice                          |
           |  Please ensure the above setting is your preference. |
           |   For better reliability and optimized performance   |
           |     please execute the Installation Utility          |
           |       to reconfigure your device driver              |
           +------------------------------------------------------+

         Where the operating mode and speed parameter may vary with the
         hard drive(s) attached. This message will be shown when user
         defined parameter is entered with the DOS device driver. The
         Installation Utility stands for the VLIDE.EXE.




     +==========================================================+
     |  VL-IDE device driver for Microsoft Windows version 3.1  |
     +==========================================================+

     The file VLIDE.386 is the Microsoft Windows 3.1 disk driver for the
     VL-IDE disk controller.

     While Microsoft Windows version 3.1 supports 32-bit disk access, the
     disk data transfer between host and the IDE adapter is still limited
     by the 16-bit ISA bus. If you want to speed up your hard drives under
     Windows through the 32-bit VL-Bus, you will need this driver. In
     addition, the driver also allows your host to access the disk data
     through the faster "read/write multiple" commands.

     If you choose to install the Windows' driver manually,
     you should follow the steps below:


     1. Copy the driver VLIDE.386 to your system in the appropriate path.

        It is recommended that the driver VLIDE.386 be copied to the Windows
        SYSTEM directory.

     2. Check if the following lines exist in the [386Enh] section of your
        SYSTEM.ini file.

        [386Enh]
        32BitDiskAccess=ON
        device=*int13

        If the statements do not exist, add them into the [386Enh] section.
        If the statements exist, but 32BitDiskAccess is set to "OFF", you
        need to change it to "ON".


     3. Delete the "device=*wdctrl" device setting.

        Delete the command line "device=*wdctrl" from the [386Enh] section
        of your SYSTEM.INI file, if it exists.

     4. Install the virtual device "VLIDE.386".

        Add the following command lines in the [386Enh] section of the
        SYSTEM.INI file:

              device=[drive:][\path\]VLIDE.386
              DisksAccessMode=[Fast or Turbo] [/W] [/D0:n] [/D1:m]

        The [drive:] and [\path\] point to the directory that contains
        VLIDE.386 file. Note that the setting must specify the full path
        of the device driver VLIDE.386.

        The setting of disk_access_mode specifies the disk access mode as
        follows:

              Fast  : VL-IDE controller working in the Fast mode
              Turbo : VL-IDE controller working in the Turbo mode (default)
              W     : VL-IDE controller working in the 16 bit data access mode
              D0    : drive 0 speed setting
              n     : drive 0 speed from 0 to 7
              D1    : drive 1 speed setting
              m     : drive 1 speed from 0 to 7

              Note  : If no parameter is specified, the VL-IDE disk controller
                      will be set to run under the default Turbo and 32 bit
                      data access mode.

        Under Fast mode, the VL-IDE supports 32-bit VL-Bus IO. Under Turbo
        mode, the VL-IDE not only supports 32-bit VL-Bus IO, it also supports
        the read/write multiple commands. Since read/write multiple commands
        allow the host to access disk data in multiple-sector blocks, the Turbo
        mode will usually be faster.

        Note: Not all IDE drives support the read/write multiple commands.
        Usually, you may set your VL-IDE to run under the Turbo mode. When
        your system is brought up, the driver VLIDE.386 will automatically
        issue an Identify Drive command to check if the attached IDE drive(s)
        support the read/write multiple commands. In case your drive(s) does
        not support the read/write multiple commands, the VL-IDE controller
        will automatically be forced to run under the Fast mode.

        Note: Some IDE drives may not support the read/write multiple commands
        properly. If your VL-IDE disk controller can not access the attached
        drive(s) properly under the default Turbo mode, you have to specify
        the parameter explicitly as "Fast".


     +========================================================+
     |  Netware 3.xx & 4.01 disk driver for VL-IDE Controller |
     +========================================================+

     It's assumed that you are familiar with Netware installation. If this
     is not the case, you may wish have someone else help check your work.

     Please  follow the  steps below  to install the driver for Netware 3.10.
     Use VLIDE311.DSK (or VLIDE401.DSK) instead of VLIDE310.DSK in the
     following procedure when you are installing Netware 3.11 (or 4.01).
     Note that you don't need to load the ISADISK.DSK when you are installing
     the Netware driver for VL-IDE disk controller.

      1.  After you have installed the VL-IDE disk controller, bring up the
          Netware server until the prompt ":" appears on the screen.

      2.  Type the following command after the ":" prompt:

          :load VLIDE310 [/F or /T] [/W] [/D0:n] [/D1:m] port=1f0 int=e

          The parameters F, T and W define the operating mode. The parameters
          D0, n, D1 and m define the speed setting for the attached IDE drives.

           F   : VL-IDE controller working in the Fast mode
           T   : VL-IDE controller working in the Turbo mode (default )
           W   : VL-IDE controller working in the 16 bit data access mode
           D0  : drive 0 speed setting
           n   : drive 0 speed from 0 to 7
           D1  : drive 1 speed setting
           m   : drive 1 speed from 0 to 7

         Usually, you do not need to enter any speed parameters during the
         installation process. Since when you execute the VLIDE.EXE to
         install the DOS driver, the device drivers for Netware are also
         reconfigured for the optimal speed setting.

         Note: If no operating mode parameter is specified, the VL-IDE
         controller will be set to run under the default Turbo and 32 bit
         data access mode.

       Under Fast(F) mode, the VL-IDE controller supports 32-bit VL-Bus IO.
       Under Turbo (T) mode, the VL-IDE controller not only supports 32-bit
       VL-Bus IO, it also supports the read/write multiple commands. Since
       read/write multiple commands allow the host to access disk data in
       multiple-sector blocks, the Turbo mode will usually be faster.

       Note that not all IDE drives support the read/write multiple commands.
       Usually, you may set your VL-IDE controller to run under the Turbo
       mode. When your system is brought up, the driver will automatically
       issue an Identify Drive command to check if the attached IDE drive(s)
       support the read/write multiple commands. In case your drive(s) does
       not support the read/write multiple commands, the VL-IDE controller
       will automatically be forced to run under the Fast mode.

       Note: Some IDE drives may not support the read/write multiple commands
       properly. If your VL-IDE disk controller can not access the attached
       drive(s) properly under the default Turbo mode, you have to specify
       the parameter as "F" explicitly.


     +===========================================================+
     | IBM OS/2 2.x disk driver for VL-IDE VL-Bus IDE Controller |
     +===========================================================+

     VLIDE.ADD is the driver for IBM OS/2 2.0 and IBM OS/2 2.1.

     Your VL-IDE disk controller needs this device driver to take the
     advantage of the high performance 32-bit VL-Bus when running under
     OS/2.

     Please follow the steps below in installing the driver for the
     VL-IDE disk controller.

     1. Install the OS/2 driver.

        Copy VLIDE.ADD to the OS2 directory of your system.

        Use a text editor to edit the CONFIG.SYS file. Add the
        following line:


        BASEDEV = VLIDE.ADD [/A:0 [/U:0 /SPEED:n] [/U:1 /SPEED:m]]

        Note: This line must not contain either drive or path
              information.

        parameters:

         A:       adapter number
         U:       drive number
         SPEED:   drive speed setting
         n:       speed of drive 0 from 0 to 15
         m:       speed of drive 1 from 0 to 15

        Example:

        If you want your VL-IDE controller to run with drive 0 speed
        3 and drive 1 speed 5. Please add the following statement to
        the file CONFIG.SYS.

          BASEDEV = VLIDE.ADD /A:0 /U:0 /SPEED:3 /U:1 /SPEED:5

     2. Delete the "BASEDEV = IBM1S506.ADD" device setting.

        Delete the command line "BASEDEV = IBM1S506.ADD" from
        the CONFIG.SYS file, if it exists.

     3. Reboot the system.


     +===================================================================+
     |  Microsoft Windows NT version 3.1 disk driver                     |
     |  for VL-IDE Disk Controller                                       |
     +===================================================================+

     You only need this driver if you want to install TURBO mode
     under Windows NT.

     Please follow the steps below to install the driver.

     1. Copy the following files to a formatted diskette:

           . VLIDENT.SYS
           . CITURBO.EXE
           . NTINS.BAT
           . NTUNINS.BAT
           . PTIREG.EXE
           . PTIUREG.EXE

     2. Boot with Windows NT.

     3. Insert the diskette into drive A:.

     4. Type the following command in the "Command Prompt" window:

           A:\NTINS

        Then the driver will install automatically.


     ******** Changing Operating Mode *******

     If you want to change the operating mode, please type the following command:

           CITURBO

     The following message will be shown on the screen to ask you which mode
     will be set:

            Will the controller be in TURBO or FAST mode
            (T/F)? (default=T)

     Please answer 'T' or 'F' for your setup.

     After the changes have been made, please do a hard boot of the system.


     +=============================+
     |  Trademark Acknowledgments  |
     +=============================+

     VESA is a registered trademark of the Video Electronics Standards
     Association. VL-Bus is a trademark of the Video Electronics Standards
     Association.

     MS-DOS and Windows are registered trademarks of Microsoft Corporation.
     PC, PC-AT and OS/2 are registered trademarks of IBM Corporation.
     Unix is a registered trademark of American Telephone and Telegraph Corp.
     Netware is a registered trademark of Novell Corporation.


