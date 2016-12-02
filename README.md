# Test Extensions For VS2017

Both extension projects in this repository were created from the default VSIX project template in Visual Studio 2015. VSSDK RC2 build tools nuget package was then added to the projects, and both are configured in a similar fashion to GHfVS:

- using the latest VSSDK build tools (RC2)
- IsProductComponent csproj flag
- specifying CoreEditor as a prerequisite
- installing for AllUsers

[ExtensionFor2015And2017](ExtensionFor2015And2017/) targets both VS2015 and VS2017 (just like GHfVS), and it only includes the VSSDK build tools as a dependency, nothing else.

This project initially failed to deploy to the experimental instance with:

```
1>C:\Users\shana\Documents\GitHub\VisualStudio\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error VSSDK1077: Unable to locate the extensions directory. "Value cannot be null.
1>C:\Users\shana\Documents\GitHub\VisualStudio\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error VSSDK1077: Parameter name: path1".
```

After clearing the nuget cache, it now fails with:

```
1>------ Rebuild All started: Project: ExtensionFor2015And2017, Configuration: Debug Any CPU ------
1>  ExtensionFor2015And2017 -> C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\ExtensionFor2015And2017\bin\Debug\ExtensionFor2015And2017.vsix
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: The "GetExtensionsPath" task failed unexpectedly.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. The system cannot find the file specified.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: File name: 'Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:    at Microsoft.VsSDK.Build.Tasks.GetExtensionsPath.Execute()
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:    at Microsoft.Build.BackEnd.TaskExecutionHost.Microsoft.Build.BackEnd.ITaskExecutionHost.Execute()
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:    at Microsoft.Build.BackEnd.TaskBuilder.<ExecuteInstantiatedTask>d__26.MoveNext()
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: 
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: === Pre-bind state information ===
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: DisplayName = Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:  (Fully-specified)
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Appbase = file:///C:/Program Files (x86)/MSBuild/14.0/bin/
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Initial PrivatePath = NULL
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: Calling assembly : Microsoft.VsSDK.Build.Tasks, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: ===
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: This bind starts in LoadFrom load context.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: WRN: Native image will not be probed in LoadFrom context. Native image will only be probed in default load context, like with Assembly.Load().
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Using application configuration file: C:\Program Files (x86)\MSBuild\14.0\bin\MSBuild.exe.Config
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Using host configuration file: 
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Using machine configuration file from C:\Windows\Microsoft.NET\Framework\v4.0.30319\config\machine.config.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Post-policy reference: Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2015And2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2015And2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2015And2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2015And2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2015And2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: 
========== Rebuild All: 0 succeeded, 1 failed, 0 skipped ==========
```


[ExtensionFor2017](ExtensionFor2017/) targets only VS2017 and has a Package subclass implementation, with all its required dependencies bumped to the latest nuget versions.

Packaging this project fails with:

```
1>------ Rebuild All started: Project: ExtensionFor2017, Configuration: Debug Any CPU ------
1>  ExtensionFor2017 -> C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\ExtensionFor2017\bin\Debug\ExtensionFor2017.dll
1>  ExtensionFor2017 -> C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\ExtensionFor2017\bin\Debug\ExtensionFor2017.vsix
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: The "GetExtensionsPath" task failed unexpectedly.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. The system cannot find the file specified.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: File name: 'Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:    at Microsoft.VsSDK.Build.Tasks.GetExtensionsPath.Execute()
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:    at Microsoft.Build.BackEnd.TaskExecutionHost.Microsoft.Build.BackEnd.ITaskExecutionHost.Execute()
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:    at Microsoft.Build.BackEnd.TaskBuilder.<ExecuteInstantiatedTask>d__26.MoveNext()
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: 
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: === Pre-bind state information ===
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: DisplayName = Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018:  (Fully-specified)
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Appbase = file:///C:/Program Files (x86)/MSBuild/14.0/bin/
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Initial PrivatePath = NULL
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: Calling assembly : Microsoft.VsSDK.Build.Tasks, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: ===
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: This bind starts in LoadFrom load context.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: WRN: Native image will not be probed in LoadFrom context. Native image will only be probed in default load context, like with Assembly.Load().
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Using application configuration file: C:\Program Files (x86)\MSBuild\14.0\bin\MSBuild.exe.Config
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Using host configuration file: 
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Using machine configuration file from C:\Windows\Microsoft.NET\Framework\v4.0.30319\config\machine.config.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Post-policy reference: Microsoft.VisualStudio.Settings.15.0, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Program Files (x86)/MSBuild/14.0/bin/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.DLL.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: LOG: Attempting download of new URL file:///C:/Users/shana/Source/Repos/2017ExtensionsTest/ExtensionFor2017/packages/Microsoft.VSSDK.BuildTools.15.0.25929-RC2/tools/VSSDK/Microsoft.VisualStudio.Settings.15.0/Microsoft.VisualStudio.Settings.15.0.EXE.
1>C:\Users\shana\Source\Repos\2017ExtensionsTest\ExtensionFor2017\packages\Microsoft.VSSDK.BuildTools.15.0.25929-RC2\tools\VSSDK\Microsoft.VsSDK.targets(612,5): error MSB4018: 
```
