---
title: "Проверка подтипы проекта во время выполнения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подтипы проектов"
  - "Проверьте подтипы"
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Проверка подтипы проекта во время выполнения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage, который зависит от подтип пользовательский проект должен включать логики, чтобы искать подтипа таким образом, чтобы он не удается корректно Если подтип не указан. Ниже показано, как проверить наличие подтипом указанного.  
  
### Чтобы убедиться в наличии подтипа  
  
1.  Объекты проекта и решения, как получить иерархии проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта, добавив следующий код в VSPackage.  
  
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
  
4.  Проверьте список подтипом указанного идентификатора GUID.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## См. также  
 [Подтипы проектов](../extensibility/internals/project-subtypes.md)   
 [Подтипы разработки проекта](../extensibility/internals/project-subtypes-design.md)   
 [Свойства и методы дополнено подтипы проектов](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)