# Win7_SDK_Samples
Windows 7 SDK Sample Applications
#Samples in the Windows SDK
This page provides information on working with the samples that are included in the Windows SDK.  For known issues with individual samples, please refer to the Release Notes included with the SDK or the updated version which is posted online.
The Windows SDK samples cover numerous technology areas.  The SDK includes samples that use managed code and those that primarily use native code, to provide working examples of code for developers at all levels to experiment with and learn from.
.NET Framework (managed code) Samples
The .NET Framework 4 samples do not ship with the Windows SDK for Windows 7 and .NET Framework 4.  They can be downloaded from Code Gallery.
Win32 (native code) Samples
The Windows samples demonstrate Windows operating system features primarily using native code. These unmanaged Win32 samples are not included in the documentation. They are installed as loose files under the default samples location C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples. This content can be deselected during SDK setup. A few samples with some managed code (PowerShell, Tablet PC, and a few others) install with the Win32 samples.
The Win32 samples directory layout for the Windows SDK is:
\Begin
\Com
\DataAccess
\Multimedia
\NetDS
\Security
\SysMgmt
\TabletPC
\Touch
\Web
\WinBase
\WinUI
\XPS
#Building Samples
Building Samples Using Visual Studio 2010 or Windows SDK v7.1 (MSBuild 4.0)
Visual Studio 2010 and the Windows SDK v7.1 use the MSBuild 4.0 build environment.  The Visual C++ compilers shipped in the Windows SDK v7.1 are the same compilers that shipped in Visual Studio 2010.  All Win32 (native) sample project files in the Windows SDK v7.1 must be upgraded prior to building using the MSBuild 4.0 environment.
 
Moving From the VCBuild to the MSBuild 4.0 Environment
Visual C++ 2010 moved to newer build system (MSBuild v4.0) to provide better performance, scalability and extensibility. In order for the build system migration to happen the project file format in Visual C++ 2010 had to change to a different format in order to be compatible with the new MSBuild v4.0 file format (earlier versions of Visual C++ have used VCBuild as their build system).  The extension of the new Visual C++ 2010 project file has been changed from “.vcproj” to “.vcxproj”.  Project files with the “.vcproj” extension can be upgraded using the vcupgrade tool (included in this release of the SDK).  For more information on how to upgrade a project file.
 
Setting Build Environment Switches
To set specific targets in the build environment:
·          Launch the Windows SDK build environment - From the Start menu, click on  All Programs > Microsoft Windows SDK v7.1 > Windows SDK 7.1 Command Prompt
·          Set the build environment -  At the prompt, type: setenv  [/Debug | /Release][/x86 | /x64 | /ia64 ][/vista | /xp | /2003 | /win7][-h | /?]
The setenv.cmd help [-h | /?] displays the usage
                /Debug   - Create a Debug configuration build environment
                /Release - Create a Release configuration build environment
                /x86     - Create 32-bit x86 applications
                /x64     - Create 64-bit x64 applications
                /ia64    - Create 64-bit ia64 applications
                /vista   - Create Windows Vista SP1 applications or Windows Server 2008
                /xp      -   Create Windows XP applications
                /2003    - Create Windows Server 2003 applications
               /win7    - Create Windows 7 or Windows Server 2008 R2 applications
 
#Upgrading Projects to Visual C++ 2010
The Windows SDK for Windows 7 and .NET Framework 4 installs the vcupgrade.exe tool which will convert the previous project file format to the MSBuild compatible project file format. In this process the extension of the project file (.vcproj) will change to .vcxproj.  To upgrade a Visual C++ 2005 or a Visual C++ 2008 (ex: sample.vcproj) file to VC 2010 (sample.vcxproj) file format in the SDK build environment, at the command prompt type: “vcupgrade sample.vcproj”.
Usage:
VCUpgrade [options] <project file>
Options:
     -nologo                     Suppresses the copyright message
     -nocolor                    Do not output error and warning messages in color
     -overwrite                Overwrite existing files
     -PersistFramework  Keep the Target Framework Version while upgrading. (-p)
The vcupgrade tool can upgrade any project version from VC6 through VC 2008 to the VC 2010 format, and returns a success message if the conversion succeeded.  If unsuccessful, a message listing conversion errors is returned.
 
VB, C# Applications Using MSBuild 4
The .NET Framework 4 installs the C# (csc.exe) and Visual Basic (vbc.exe) compilers and the respective property and target files as required by MSBuild 4.0. The Windows SDK for Windows 7 and .NET Framework 4 build environment will support building using MSBuild 4.0 while targeting C# and Visual Basic applications.
To Use the C# (csc.exe) and Visual Basic (vbc.exe) compiler directly to compile a single file for Visual Studio 2008 and Visual Studio 2010:
·          From a command line type:
o    Csc.exe *.cs (for CSharp)
o    vbc.exe *.vb (for Visual Basic)
Using MSBuild 4.0 to build a project or solution file:
·          From an SDK command line type:
o    Msbuild *.csproj (for CSharp)
o    Msbuild *.vbproj (for Visual Basic)
o    Msbuild *.sln (for a Solution file)
 
#Updating Visual Studio to Use the Windows SDK v7.1 Components
 If you are using Visual Studio 2005, 2008, or 2010 and would like to utilize the Windows SDK v7.1 components, you can use an automated tool (include with the SDK) to point to the Windows SDK v7.1 components (Windows headers and libraries, tools, reference assemblies).  See below for How To:
How To: Using the Windows SDK Configuration Tool (GUI) With Visual Studio 2005/2008
Visual Studio 2005/2008 users can run the Windows SDK Configuration Tool (GUI) to utilize the Windows SDK v7.1 components.  The functionality of the Windows SDK Configuration Tool has not changed from that which was released in the Windows 7 RTM SDK.
1.     On your PC, click the Windows Start button
2.     Click All Programs
3.     Click Microsoft Windows SDK v7.1
4.     Click Visual Studio Registration
5.     Right click Windows SDK Configuration Tool and Select Run as administrator
6.     Once the Windows SDK Configuration Tool is running, select v7.1 from the Installed Windows SDK Versions dropdown
7.     Click the Make Current button
#How To: Using the Windows SDK Configuration Tool (Command Line) With Visual Studio 2008
Visual Studio 2008 users can run the Windows SDK Configuration Tool (Command Line) to utilize the Windows SDK v7.1 components.  The functionality of the Windows SDK Configuration Tool has not changed from that which was released in the Windows 7 RTM SDK.
NOTE:  This is not a supported scenario with Visual Studio 2005.
1.     On your PC, click the Windows Start button
2.     Click All Programs
3.     Click Microsoft Windows SDK v7.1
4.     Right click Windows SDK 7.1 Command Prompt and Select Run as administrator
5.     Change directories (cd) to \Program Files\Microsoft\Windows\v7.1\Setup>
6.     Type:  WindowsSdkVer.exe -version:v7.1
How To: Using the Platform Toolset With Visual Studio 2010
Visual Studio 2010 users can make use of the new Native Multitargeting functionality of the Platform Toolset to target the Windows SDK v7.1 components. 
1.     Start Visual Studio 2010
2.     In the Visual Studio IDE, open a solution file (*.sln)
3.     In Solution Explorer, right click the solution file and select Properties
4.    Select Configuration Properties, General from the list in the left pane
5.     Select All Configurations in the Configuration dropdown
6.     Select Windows7.1SDK in the Platform Toolset option in the right pane under the General category.
7.     Click the Ok button
 
#Upgrading Projects to Visual C++ 2010
The Windows SDK for Windows 7 and .NET Framework 4 installs the vcupgrade.exe tool which will convert the previous project file format to the MSBuild compatible project file format. In this process the extension of the project file (.vcproj) will change to .vcxproj.  To upgrade a Visual C++ 2005 or a Visual C++ 2008 (ex: sample.vcproj) file to VC 2010 (sample.vcxproj) file format in the SDK build environment, at the command prompt type: “vcupgrade sample.vcproj”.
 
Usage:
VCUpgrade [options] <project file>
 
Options:
     -nologo                    Suppresses the copyright message
     -nocolor                   Do not output error and warning messages in color
     -overwrite                Overwrite existing files
     -PersistFramework    Keep the Target Framework Version while upgrading. (-p)
 
The vcupgrade tool can upgrade any project version from VC6 through VC 2008 to the VC 2010 format, and returns a success message if the conversion succeeded.  If unsuccessful, a message listing conversion errors is returned.
Building with the Windows 7 headers, libraries, and tools
In order to utilize Windows SDK headers, libraries, and tools from within the Windows SDK command line build environment or from within Visual Studio 2005/2008 build environments, the SDK-provided Windows SDK Configuration Tool must be run. The Windows SDK Configuration Tool must be run for each user on Windows Vista or later.
You can build Win32 applications out-of-the-box with the Vista SDK components that are embedded in Visual Studio 2008. You can switch to the more recent components that ship with the Windows SDK for Windows 7 by using the Windows SDK Configuration Tool.
To run the Windows SDK Configuration Tool, go to Start > All Programs > Microsoft Windows SDK v7.0 > Visual Studio Registration > Windows SDK Configuration Tool.
Upgrading C++ Sample Project Files for Visual Studio 2008 or the VC++ 9.0 Compilers
To build samples in either the SDK command line build environment or in Microsoft Visual Studio 2008, some samples project files must be upgraded. This step is not necessary when building in Visual Studio 2005. This is because some samples in the SDK ship with native Visual Studio 2005 project files that must be upgraded to work with the compilation system shipped in the Windows SDK, which is the same version as shipped in Visual Studio 2008 SP1.
To upgrade the project in the current directory, type vcbuild /upgrade or devenv /upgrade in the SDK Build environment.
Microsoft .NET Framework sample project files cannot be upgraded using the workaround above. The files must be upgraded using vcbuild /upgrade /overrideRefVer SampleName.vcproj. Visual Studio must be installed in order for this command to work.  The upgrade /overriderefver switch indicates that it will use the .NET Framework.
ATL/MFC Dependency
Some samples require ATL and/or MFC headers, libraries, or runtime, which are included with Visual C++ (non-Express editions).
How to: Build from the Windows SDK Command Line
This guide demonstrates how to build a sample or application from the Windows SDK command line.
1.     Copy your application or sample to a working folder not under \Program Files.
2.     Open the Windows SDK CMD shell (Start → All Programs → Windows SDK v7.0 → SDK CMD Shell).
3.     Navigate to the directory where your sample or application can be found.
4.     Build a sample or project from the command line as follows, depending upon the type of project file:
·         Build a makefile by typing nmake
·         Build a .csproj file by typing msbuild *.csproj /p:platform=[ win32 | X64 | IA64]
·         Build a .vbproj file by typing msbuild *.vbproj /p:platform=[ win32 | X64 | IA64]
·         Build a .sln file by typing msbuild *.sln /p:platform=[ win32 | X64 | IA64]
·         Build a .vcxproj by typing vcbuild *.vcxproj /platform=[ win32 | X64 | IA64 ]
When building with msbuild, you should specify a target platform. If a project is configured to build for several different platform types and you do not specify which platform you want to build for, the first platform listed in the solution or project file will be built. Configurations are listed in alphabetical order by Visual Studio, so "Itanium" might be the first configuration listed.
If you want to build an application configured for an X86 machine, specify "win32":
msbuild mysample.vbproj /p:platform=win32
If you want to build an application configured for an X64 machine, specify "X64":
msbuild mysample.vbproj /p:platform=X64
If you want to build an X64 application, but your project does not have an X64 configuration, see How to: Add 64-Bit Support to VC Project Files.
#How to: Set Build Environment Switches
To set the Windows 7 SDK command line build environment, use the setenv.cmd tool within a debug cmd shell by following the steps below.
1.     Launch the Windows SDK build environment. From the Start menu, click on All Programs > Microsoft Windows SDK v7.0 > CMD Shell.
2.     Set the build environment. At the prompt, type: "C:\Program Files\Microsoft SDKs\Windows\v7.0\Bin\setenv.cmd" [/target]
The list of available targets is shown below.
Usage: "Setenv [/Debug | /Release][/x86 | /x64 | /ia64][/vista | /xp | /2003 | / 2008 /win7 ] [-h or /?]"
/Debug - Create a Debug configuration build environment
/Release - Create a Release configuration build environment
/x86 - Create 32-bit x86 applications
/x64 - Create 64-bit x64 applications
/ia64 - Create 64-bit IA64 applications
/vista - Windows Vista applications
/xp - Create Windows XP SP2 applications
/2003 - Create Windows Server 2003 applications
/2008 - Create Windows Server 2008 or Windows Vista SP1 applications
/win7 - Create Windows 7 applications
#How to: Use the DirectX SDK when Visual Studio 2008 is installed
In order to utilize DirectX SDK resources when using MSBuild in the Windows SDK build environment, you should ensure that the DirectX SDK include, library, and executables directories are set correctly in Visual Studio 2008. The order in which Visual Studio 2008 looks for executable directories and library files is important. The Windows SDK directories should appear above the DirectX SDK directories.
1.     Launch Visual Studio 2008.
2.     Open the Tools menu and select Options…. The Options dialog box appears.
3.     In the left pane of the Options dialog box, expand the Projects and Solutions node.
4.     Under Project and Solutions, select VC++ Directories.
5.     In the right pane, set the "Platform" drop-down list box to Win32® and the "Show directories for" drop-down list box to "Executable" files.
6.     At the bottom of the list of executable file directories, create a new entry for the DirectX SDK: [drive]:\Program Files\Microsoft DirectX SDK [version]\Utilities\bin\x86 (If there is already such an entry, move it to the bottom of the list.)
7.     Set the "Show directories for" drop-down list box to "Include" files.
8.     At the bottom of the list of directories, create a new entry for the DirectX SDK: [drive]:\Program Files\Microsoft DirectX SDK [version]\Include (If there is already such an entry, move it to the bottom of the list.)
9.     Set the "Show directories for" drop-down list box to "Library" files.
10.     At the bottom of the list of directories, create a new entry for the DirectX SDK: [drive]:\Program Files\Microsoft DirectX SDK [version]\Lib (If there is already such an entry, move it to the bottom of the list.)
11.     If you are developing an application to run on AMD64, you should repeat these steps to set the AMD64 paths by setting the "Platform" drop-down list box to AMD64 and providing the appropriate paths.
12.     Click OK.
#How to: Add 64-Bit Support to VC Project Files
Not all samples in the Windows SDK have project files configured out-of-the-box for 64-bit support, but you can quickly and easily configure those samples to target 64-bit platforms. This guide shows how to accomplish this development by using the project configurations available in the Visual Studio Integrated Development Environment (IDE).
To develop 64-bit applications, you must install one or both of the Visual C++ 64-bit compilers. Without these compilers on your development machine, 64-bit project configurations will not be available in the Visual Studio IDE. For more information, see Installing Visual Studio 64-bit Components on MSDN.
First, this guide describes how to change the active project configuration to target 64-bit platforms using the Visual Studio IDE. Next, the guide describes how to migrate Win32® project settings into a 64-bit project configuration.
To set up C++ applications to target 64-bit platforms
1.     Using Visual Studio, open the C++ project that you want to configure to target a 64-bit platform.
2.     Open the property pages for that project. (Right-click the project node in Solution Explorer and click Properties.)
3.     Click Configuration Manager to open the Configuration Manager Dialog Box.
4.     Click the Active Solution Platform list, and then select the <New…> option to open the New Solution Platform Dialog Box.
5.     Click the Type or select the new platform drop-down arrow, and then select a 64-bit platform. (The 64-bit platforms will not be available if you do not have a 64-bit compiler installed.) In the New Solution Platform dialog box, you can copy existing project settings into the new 64-bit project configuration using the Copy settings.
6.     Click OK. The platform you selected in the preceding step will appear under Active Solution Platform in the Configuration Manager dialog box.
7.     Click Close in the Configuration Manager dialog box, and then click OK in the <Projectname> Property Pages dialog box.
To copy Win32 project settings into a 64-bit project configuration
·         When the New Solution Platform dialog box is open while you set up your project to target a 64-bit platform, click the Copy settings from the drop-down arrow, and then select Win32. The project settings listed below are automatically updated on the project level:
·         /MACHINE (Specify Target Platform) is set to /MACHINE:IA64 or /MACHINE:X64.
·         Register Output is turned OFF. For more information, see Linker Property Pages.
·         Target Environment is set to /env x64 or /env ia64. For more information, see MIDL Property Pages: General.
·         Validate Parameters is cleared and reset to the default value. For more information, see MIDL Property Pages: Advanced.
·         If Debug Information Format was set to /ZI in the Win32 project configuration, it is set to /Zi in the 64-bit project configuration. For more information, see /Z7, /Zi, /ZI (Debug Information Format).
·         Values of WIN32 are replaced by WIN64 for /D (Preprocessor Definitions).
Note: none of these project properties are changed if they are overridden at the file level.
Additional Troubleshooting
##For issues not covered here, refer to the Windows SDK for Windows 7 Release Notes.
