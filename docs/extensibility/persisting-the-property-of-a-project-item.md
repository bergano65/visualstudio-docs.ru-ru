---
title: Сохранение свойств элемента проекта | Документы Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6b0bc529e01d8ef34b6959b98d773857000ec1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138058"
---
# <a name="persisting-the-property-of-a-project-item"></a>Сохранение свойств элемента проекта
Можно сохранить свойства, добавленные в элемент проекта, например автору исходного файла. Это можно сделать путем сохранения свойство в файле проекта.

 Является первым шагом для сохранения свойства в файле проекта для получения иерархии проекта в качестве <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса. Этот интерфейс можно получить с помощью автоматизации или с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. После получения интерфейс, его можно использовать для определения, какой элемент проекта в данный момент выбран. Получив идентификатор элемента проекта, можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> для добавления свойств.

 В следующих процедурах можно сохранить свойство VsPkg.cs `Author` со значением `Tom` в файле проекта.

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Для получения иерархии проекта с помощью объекта DTE

1.  В пакете VSPackage, добавьте следующий код:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Чтобы сохранить свойства элемента проекта с помощью объекта DTE

1.  Добавьте следующий код в код в метод в предыдущей процедуре:

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

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Для получения иерархии с помощью IVsMonitorSelection

1.  В пакете VSPackage, добавьте следующий код:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Для сохранения выбранного проекта свойство элемента, заданного иерархии проекта

1.  Добавьте следующий код в код в метод в предыдущей процедуре:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>Чтобы убедиться, что свойство сохраняется

1.  Запустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и откройте или создайте решение.

2.  Выберите проект, элемент VsPkg.cs в **обозревателе решений**.

3.  Используйте точки останова или в противном случае определить загрузку пакета VSPackage и что SetItemAttribute выполняется.

    > [!NOTE]
    > Вы можете autoload VSPackage в контексте пользовательского интерфейса <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Дополнительные сведения см. в разделе [загрузке пакетов VSPackage](../extensibility/loading-vspackages.md).

4.  Закрыть [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и откройте в блокноте файл проекта. Вы увидите \<Автор > тег со значением Tom, следующим образом:

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>См. также

- [Настраиваемые средства](../extensibility/internals/custom-tools.md)