---
title: Сохранение свойства элемента проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842588"
---
# <a name="persisting-the-property-of-a-project-item"></a>Сохранение свойства элемента проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Может потребоваться сохранить свойство, добавляемое в элемент проекта, например автор исходного файла. Это можно сделать, сохранив свойство в файле проекта.  
  
 Первым шагом сохранения свойства в файле проекта является получение иерархии проекта в качестве <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса. Этот интерфейс можно получить либо с помощью службы автоматизации, либо с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . После получения интерфейса его можно использовать для определения того, какой элемент проекта выбран в данный момент. После получения идентификатора элемента проекта можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> для добавления свойства.  
  
 В следующих процедурах сохраняется свойство VsPkg.cs `Author` со значением `Tom` в файле проекта.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Получение иерархии проекта с помощью объекта DTE  
  
1. Добавьте следующий код в VSPackage:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Сохранение свойства элемента проекта с помощью объекта DTE  
  
1. Добавьте следующий код в код, указанный в методе в предыдущей процедуре:  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Получение иерархии проекта с помощью Ивсмониторселектион  
  
1. Добавьте следующий код в VSPackage:  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Сохранение выбранного свойства элемента проекта с учетом иерархии проекта  
  
1. Добавьте следующий код в код, указанный в методе в предыдущей процедуре:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Проверка сохранения свойства  
  
1. Запустите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , а затем откройте или создайте решение.  
  
2. Выберите элемент проекта VsPkg.cs в **Обозреватель решений**.  
  
3. Используйте точку останова или иным образом определите, что пакет VSPackage загружен и выполняется Сетитематтрибуте.  
  
    > [!NOTE]
    > Пакет VSPackage можно автозагрузки в контексте пользовательского интерфейса <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Дополнительные сведения см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
4. Закройте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , а затем откройте файл проекта в блокноте. Вы увидите \<Author> тег со значением Tom, как показано ниже:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Настраиваемые средства](../extensibility/internals/custom-tools.md)
