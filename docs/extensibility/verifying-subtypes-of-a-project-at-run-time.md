---
title: Проверка подтипов проекта во время выполнения (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698174"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Проверка подтипов проекта во время выполнения
VSPackage, который зависит от пользовательского подтипа проекта, должен включать логику для поиска этого подтипа, чтобы он мог не быть грациозно, если подтип не присутствует. Следующая процедура показывает, как проверить наличие указанного подтипа.

### <a name="to-verify-the-presence-of-a-subtype"></a>Проверить наличие подтипа

1. Получите иерархию проекта из объектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> проекта и решения в качестве объекта, добавив следующий код в ваш VSPackage.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Отбросьте иерархию в <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> интерфейс.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Получите список GUID типа проекта, <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>ссылаясь на .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Проверьте список для GUID указанного подтипа.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>См. также
- [Подтипы проекта](../extensibility/internals/project-subtypes.md)
- [Проектирование подтипов проекта](../extensibility/internals/project-subtypes-design.md)
- [Свойства и методы, расширенные подтипами проектов](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
