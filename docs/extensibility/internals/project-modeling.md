---
title: "Проект моделирования | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "автоматизация [Visual Studio SDK] реализации объектов проекта"
  - "проект модели, автоматизации"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Проект моделирования
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Следующий шаг в защите автоматизации проекта реализовать стандартные объекты проекта:  <xref:EnvDTE.Projects> и  `ProjectItems` коллекции.   `Project` и  <xref:EnvDTE.ProjectItem> объекты; остальные объекты и уникальны для реализации.  Эти стандартные объекты указываются в файле Dteinternal.h.  Реализация стандартных объектов предоставляется в образце BscPrj.  Можно использовать эти классы модели для создания собственных стандартные объекты проекта, которые стоят параллельно с объектами проекта из других типов проектов.  
  
 Объект\-получатель автоматизации предполагается возможность вызова <xref:EnvDTE.Solution>\("`<UniqueProjName>")`и  <xref:EnvDTE.ProjectItems> \(`n`where\)  n номер индекса для получения конкретного проекта в решении.  Вызовы этот автоматизации заставляет среду вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> на соответствующей иерархии проекта, передавая в качестве параметра VSITEMID\_ROOT ItemID и VSHPROPID\_ExtObject в качестве параметра VSHPROPID.  `IVsHierarchy::GetProperty` возвращает  `IDispatch` указатель на объект автоматизации, предоставляющий ядро  `Project` интерфейс, в котором реализован.  
  
 Ниже приведен синтаксис `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Проекты приспосабливают вложения и используют коллекции для создания групп в составе элементы проекта.  Иерархия выглядит следующим образом.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Вложение означает, что значение a <xref:EnvDTE.ProjectItem> объект может иметь  <xref:EnvDTE.ProjectItems> коллекция одновременно, поскольку a  `ProjectItems` коллекция может содержать вложенные объекты.  В образце базовой проекта не это демонстрирует вложение.  Путем реализации `Project` объект, участвуете в дерево\-как структура, характеризует создание общей модели автоматизации.  
  
 Автоматизация проектов выполните, в следующей схеме.  
  
 ![Объекты проекта Visual Studio](../../extensibility/internals/media/projectobjects.png "ProjectObjects")  
Автоматизация проектов  
  
 Если не реализуется a `Project` объект среда по\-прежнему возвращает универсальный шаблон  `Project` объект, содержащий только имя проекта.  
  
## См. также  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>