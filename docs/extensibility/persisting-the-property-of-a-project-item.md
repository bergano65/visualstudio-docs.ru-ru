---
title: Сохранение свойства элемента проекта | Документация Майкрософт
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
ms.openlocfilehash: da231c924e3167a50c885cf18ef878a02b28b166
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915585"
---
# <a name="persist-the-property-of-a-project-item"></a>Сохранить свойство элемента проекта
Вы можете сохранить свойства, добавляемого элемента проекта, такие как автор исходного файла. Это можно сделать путем сохранения свойства в файле проекта.

 Первым шагом для сохранения свойства в файл проекта является для получения иерархии проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс. Этот интерфейс можно получить с помощью службы автоматизации или с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. После получения интерфейс, его можно использовать для определения, какой элемент проекта выбран в данный момент. Получив идентификатор элемента проекта, можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> для добавления свойства.

 В следующих процедурах сохранения *VsPkg.cs* свойство `Author` со значением `Tom` в файле проекта.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Для получения иерархии проекта с помощью объекта DTE

1.  Добавьте следующий код к VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Сохранить свойство элемента проекта с помощью объекта DTE

1.  Добавьте приведенный ниже код в метод в предыдущей процедуре:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Для получения иерархии проекта, с помощью IVsMonitorSelection

1.  Добавьте следующий код к VSPackage:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Для сохранения выбранного проекта свойство item, учитывая иерархии проекта.

1.  Добавьте приведенный ниже код в метод в предыдущей процедуре:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Чтобы убедиться, что свойство сохраняется

1. Запустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и затем откройте или создайте решение.

2. Выберите проект элемент VsPkg.cs в **обозревателе решений**.

3. Использовать точки останова или в противном случае определить загрузку пакета VSPackage и что SetItemAttribute выполняется.

   > [!NOTE]
   > Вы можете автозагрузки VSPackage в контексте UI <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Дополнительные сведения см. в разделе [пакетов VSPackage нагрузки](../extensibility/loading-vspackages.md).

4. Закрыть [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и затем откройте файл проекта в блокноте. Вы должны увидеть \<Author > тег со значением Tom, следующим образом:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>См. также

- [Пользовательские инструменты](../extensibility/internals/custom-tools.md)