---
title: Добавление атрибута к элементу проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03faec8cdb79dcaf8bc074328da84af77d1cb17c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766867"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Добавление атрибута в элемент проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> получения и задания значений атрибутов элемента проекта. SetItemAttribute создает атрибут, если он еще не существует, добавьте его в метаданные элемента проекта.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Добавление атрибута для элемента проекта  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Чтобы добавить атрибут к элементу проекта  
  
-   В следующем коде используется <xref:EnvDTE.DTE> объект автоматизации и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> метод, чтобы добавить атрибут к элементу проекта. Идентификатор элемента проекта получается из имени элемента проекта «program.cs». Атрибут «MyAttribute» добавляется этот элемент проекта и присваивается значение «MyValue».  
  
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
  
## <a name="see-also"></a>См. также  
 [Сохранение данных в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

