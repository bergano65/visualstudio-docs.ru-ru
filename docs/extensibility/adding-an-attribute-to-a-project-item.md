---
title: Добавление атрибута для элемента проекта | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d601a4cb3a7804520f0c9c95e746275e27db4bcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="adding-an-attribute-to-a-project-item"></a>Добавление атрибута для элемента проекта
Методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> получения и задания значений атрибутов элемента проекта. SetItemAttribute создает атрибут, если он еще не существует, добавьте его в метаданных элемента проекта.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Добавление атрибута для элемента проекта  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Чтобы добавить атрибут для элемента проекта  
  
-   В следующем коде используется <xref:EnvDTE.DTE> объект автоматизации и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> метод, чтобы добавить атрибут для элемента проекта. Идентификатор элемента проекта берется из имени элемента проекта «program.cs». Атрибут «MyAttribute» добавляется этот элемент проекта и присваивается значение «MyValue».  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)