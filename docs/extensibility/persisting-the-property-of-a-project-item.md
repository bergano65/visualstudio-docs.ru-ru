---
title: Сохранение свойства элемента проекта (ru) Документы Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702212"
---
# <a name="persist-the-property-of-a-project-item"></a>Сохранение свойства элемента проекта
Может потребоваться сохранить свойство, добавленное к элементу проекта, например, автор утеса исходного файла. Это можно сделать, хранив свойство в файле проекта.

 Первым шагом к сохранению свойства в файле проекта является получение <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> иерархии проекта в качестве интерфейса. Вы можете получить этот интерфейс либо <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>с помощью автоматизации или с помощью . Как только вы получите интерфейс, вы можете использовать его, чтобы определить, какой элемент проекта в настоящее время выбран. После того, как у вас <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> есть идентификатор элемента проекта, вы можете использовать для добавления свойства.

 В следующих процедурах *VsPkg.cs* сохраняется `Author` VsPkg.cs `Tom` свойства со значением в файле проекта.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Получение иерархии проекта с объектом DTE

1. Добавьте следующий код в ваш VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Сохранение свойства элемента проекта с объектом DTE

1. Добавьте следующий код к коду, приведенному в методе предыдущей процедуры:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Для получения иерархии проекта с помощью IVsMonitorSelection

1. Добавьте следующий код в ваш VSPackage:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Сохранение выбранного свойства элемента проекта, учитывая иерархию проекта

1. Добавьте следующий код к коду, приведенному в методе предыдущей процедуры:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Проверить, сохраняется ли свойство

1. Начните, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] а затем откройте или создайте решение.

2. Выберите элемент проекта VsPkg.cs в **Solution Explorer.**

3. Используйте точку разрыва или иным образом определить, что ваш VSPackage загружается и что SetItemAttribute работает.

   > [!NOTE]
   > Вы можете автоматизать VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>в контексте uI. Для получения дополнительной [информации см.](../extensibility/loading-vspackages.md)

4. Закройте, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] а затем откройте файл проекта в блокноте. Вы должны \<увидеть автор> тег со значением Том, следующим образом:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>См. также

- [Пользовательские инструменты](../extensibility/internals/custom-tools.md)
