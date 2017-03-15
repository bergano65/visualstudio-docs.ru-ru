---
title: "Добавление атрибута в элемент проекта | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "атрибуты [Visual Studio], добавление элемента проекта"
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Добавление атрибута в элемент проекта
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> получение и установка значения атрибутов элемента проекта.  SetItemAttribute создает атрибут, если он уже не существует, то при добавлении его к метаданным элемента проекта.  
  
## Добавление атрибута к элементу проекта  
  
#### Добавление атрибута к элементу проекта  
  
-   Следующий код использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> объект автоматизации и  <xref:EnvDTE.DTE> метод, чтобы добавить атрибут к элементу проекта.  Идентификатор элемента проекта, полученные от имени "program.cs" элемента проекта.  Атрибут "MyAttribute" добавляется к данному элементу проекта и дан значение "MyValue".  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## См. также  
 [Сохранение данных в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)