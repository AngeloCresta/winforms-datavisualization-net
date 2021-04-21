# winforms-datavisualization-Net5
 Rought porting to .Net5 of [dotnet/winforms-datavisualization project](https://github.com/dotnet/winforms-datavisualization) and the [sample solution](https://github.com/AngeloCresta/winforms-datavisualization-net5/tree/main/sample) as well. 
 
# Data Visualization
[This repository](https://github.com/AngeloCresta/winforms-datavisualization-net5) contains partial source code of the `System.Windows.Forms.DataVisualization` namespace that provides charting for WinForms. 
Microsoft ported and open sourced those components to enable charting features for WinForms applications that are developed on .NET Core 3.

I've made the porting to .Net 5:
- updating references
- updating project files
- moving deprecated controls like ContextMenu, MenuItems, ... to new ones (ContextMenuStrip, ToolStripMenuItems, ...)
- ...

Application Running .Net 5:

![ApplicationRunning](https://user-images.githubusercontent.com/12256319/115564835-2480c380-a2b9-11eb-9d32-879855f5f4c3.PNG)


Hope this helps!

## Getting started with Chart Controls
The best way to learn about Chart Controls is by looking at the [sample solution](https://github.com/AngeloCresta/winforms-datavisualization-net5/tree/main/sample) where via interactive experience with the app you can learn about every chart type and every major feature. While modifying the control parameters and instantly seeing how that affects the look of the control, you can also get the generated C# or Visual Basic code to use in your apps.

![Chart Controls](sample-screenshot.png)
