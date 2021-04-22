# winforms-datavisualization .Net 5
 Rought porting to .Net5 of [dotnet/winforms-datavisualization project](https://github.com/dotnet/winforms-datavisualization) and the [sample solution](https://github.com/AngeloCresta/winforms-datavisualization-net5/tree/main/sample) as well. 
 
# Data Visualization
[This repository](https://github.com/AngeloCresta/winforms-datavisualization-net5) contains partial source code of the `System.Windows.Forms.DataVisualization` namespace that provides charting for WinForms. 
Microsoft ported and open sourced those components to enable charting features for WinForms applications that are developed on .NET Core 3.

I've made the porting to .Net 5:
- updating references
- updating project files
- moving deprecated controls like ContextMenu, MenuItems to new ones (ContextMenuStrip, ToolStripMenuItems) and relative methods
- ...

Application Running .Net 5:

![ApplicationRunning](https://user-images.githubusercontent.com/12256319/115564835-2480c380-a2b9-11eb-9d32-879855f5f4c3.PNG)

# Points of Interest

## Removed controls starting with .Net Core 3.1
Starting with .NET Core 3.1, various Windows Forms controls are no longer available. Replacement controls that have better design and support were introduced in .NET Framework 2.0. The deprecated controls were previously removed from designer toolboxes but were still available to be used ([source](https://docs.microsoft.com/en-us/dotnet/core/compatibility/3.1)).

The following types are no longer available:

**ContextMenu**
DataGrid
DataGrid.HitTestType
DataGridBoolColumn
DataGridCell
DataGridColumnStyle
DataGridLineStyle
DataGridParentRowsLabelStyle
DataGridPreferredColumnWidthTypeConverter
DataGridTableStyle
DataGridTextBox
DataGridTextBoxColumn
GridColumnStylesCollection
GridTablesFactory
GridTableStylesCollection
IDataGridEditingService
IMenuEditorService
MainMenu
Menu
Menu.MenuItemCollection
**MenuItem**
ToolBar
ToolBarAppearance
ToolBarButton
ToolBar.ToolBarButtonCollection
ToolBarButtonClickEventArgs
ToolBarButtonStyle
ToolBarTextAlign

#### RECOMMENDED ACTION
Removed control (API)|Recommended replacement
---------------------|-----------------------
ContextMenu|ContextMenuStrip	
MenuItem|ToolStripMenuItem	

That's what has been performed on the project.

## References
The [original port](https://github.com/dotnet/winforms-datavisualization) to .Net Core 3.0 used very old and still in Beta/Preview references:

![RefPackages](https://user-images.githubusercontent.com/12256319/115697948-60bd2e00-a364-11eb-96a3-4de0586dc830.PNG)

and moving away from them was a bit tricky, now they're all actualized:

![RefPack2](https://user-images.githubusercontent.com/12256319/115698475-f1940980-a364-11eb-8a2f-fa5782250268.PNG)

In a future release, maybe the use of `System.Data.SqlClient` should be avoided ...

## CSProj
The CSProj files were also modified according to the new target / Platform (Windows):

Original (Relavant Portion):
```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <AssemblyName>System.Windows.Forms.DataVisualization</AssemblyName>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
    <CLSCompliant>false</CLSCompliant>
    <NoWarn>$(NoWarn);618</NoWarn>
    <DefineConstants>$(DefineConstants);WINFORMS_CONTROL</DefineConstants>
    <!-- <Win32Manifest>Resources\System\Windows\Forms\XPThemes.manifest</Win32Manifest> -->
  </PropertyGroup>
  ```
  
Ported Version (Relavant Portion):
```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <AssemblyName>System.Windows.Forms.DataVisualization</AssemblyName>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
    <CLSCompliant>false</CLSCompliant>
    <NoWarn>$(NoWarn);618</NoWarn>
    <UseWindowsForms>true</UseWindowsForms>
    <ImportWindowsDesktopTargets>true</ImportWindowsDesktopTargets>
    <DefineConstants>$(DefineConstants);WINFORMS_CONTROL</DefineConstants>
  </PropertyGroup>
```

You have to pay attention to this directive`<UseWindowsForms>true</UseWindowsForms>`:

The UseWindowsForms property controls whether or not your application is built to target Windows Forms. 

This property alters the MSBuild pipeline to correctly process a Windows Forms project and related files. The default value is false. Set the UseWindowsForms property to true to enable Windows Forms support. You can only target the Windows platform when this setting is enabled ([source](https://docs.microsoft.com/en-us/dotnet/core/project-sdk/msbuild-props-desktop#usewindowsforms)).
    
## Getting started with Chart Controls
The best way to learn about Chart Controls is by looking at the [sample solution](https://github.com/AngeloCresta/winforms-datavisualization-net5/tree/main/sample) where via interactive experience with the app you can learn about every chart type and every major feature. While modifying the control parameters and instantly seeing how that affects the look of the control, you can also get the generated C# or Visual Basic code to use in your apps.

![Chart Controls](sample-screenshot.png)

With the sample project you can see every property and parameters in action:

![Sample1](https://user-images.githubusercontent.com/12256319/115695599-3cf8e880-a362-11eb-920f-c412780baa03.PNG)

and then copy the relavant portion of the code (C# or VB.Net):

![Sample2](https://user-images.githubusercontent.com/12256319/115695886-729dd180-a362-11eb-9662-3981e1072dd6.PNG)


## History
8th April: Initial Porting to .Net 5

Hope this helps!
