---
title: "Проверка во время выполнения подтипы проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e4ebcf8ca85c0ed6face82dfd91f8c5266013f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Проверка подтипы проекта во время выполнения
Пакет VSPackage, который зависит от подтип пользовательский проект следует логики для поиска, подтипа, чтобы он могут отклоняться корректно подтип не указан. Ниже показано, как проверить наличие указанного подтипа.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Чтобы убедиться в наличии подтипа  
  
1.  Объекты проекта и решения, как получить иерархии проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , добавив следующий код в пакете VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Приведение иерархии <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> интерфейса.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Получить список идентификаторов GUID типа проекта путем вызова <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Проверьте список для GUID указанного подтипа.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Подтипы проектов](../extensibility/internals/project-subtypes.md)   
 [Подтипы конструктора проектов](../extensibility/internals/project-subtypes-design.md)   
 [Свойства и методы, расширенные подтипами проектов](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)