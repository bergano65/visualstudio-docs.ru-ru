---
title: "Сохранение свойства элемента проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "свойства, добавление элемента проекта"
  - "элементы проекта, Добавление свойств"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Сохранение свойства элемента проекта
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Необходимо сохранять свойства, добавленные в элемент проекта, такие как автор исходного файла. Это можно сделать путем сохранения свойства в файле проекта.  
  
 Первым шагом для сохранения свойств в файле проекта должен получать иерархии проекта в качестве <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса. Этот интерфейс можно получить с помощью автоматизации или с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. После получения интерфейса, его можно использовать для определения, какой элемент проекта выбран в данный момент. Получив идентификатор элемента проекта, можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> для добавления свойства.  
  
 В следующих процедурах сохранить свойство VsPkg.cs `Author` со значением `Tom` в файле проекта.  
  
### Для получения иерархии проекта с помощью объекта DTE  
  
1.  Добавьте следующий код в VSPackage:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### Чтобы сохранить свойство элемента проекта с помощью объекта DTE  
  
1.  Добавьте следующий код в код в метод в предыдущей процедуре:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Для получения иерархии с помощью IVsMonitorSelection  
  
1.  Добавьте следующий код в VSPackage:  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### Чтобы сохранить свойство item выбранного проекта получает иерархии проекта  
  
1.  Добавьте следующий код в код в метод в предыдущей процедуре:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Чтобы убедиться, что свойство сохраняется  
  
1.  Запустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и откройте или создайте решение.  
  
2.  Выберите проект, элемент VsPkg.cs в **обозревателе решений**.  
  
3.  Использовать точки останова или в противном случае определите загрузку VSPackage и что SetItemAttribute запускается.  
  
    > [!NOTE]
    >  Вы можете автозагрузки VSPackage в контексте пользовательского интерфейса <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>. Для получения дополнительной информации см. [Загрузка пакетов VSPackages](../extensibility/loading-vspackages.md).  
  
4.  Закройте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и откройте файл проекта в блокноте. Вы должны увидеть тег \< Автор \> со значением Tom, следующим образом:  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## См. также  
 [Пользовательские инструменты](../extensibility/internals/custom-tools.md)