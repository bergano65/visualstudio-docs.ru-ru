---
title: "Предоставляя автоматизации для кода | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Объекта CodeModel"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Предоставляя автоматизации для кода
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Необходимо создать модель автоматизации пользовательского кода.  Пакет SDK для среды не предоставляет для выполнения образца.  Для решения в модели кода см. в разделе <xref:EnvDTE.CodeModel> объект.  
  
 Для реализации модели кода, необходимо реализовать все интерфейсы, определенные своей внутренней структуры данных.  Объекты должны наследовать из `IDispatch`класс.  
  
 Объекты, которые удлиняете, <xref:EnvDTE.CodeModel> и  <xref:EnvDTE.FileCodeModel>, доступные из  <xref:EnvDTE.Project> объект, и может выглядеть следующим образом:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Можно избрать для реализации просто `CodeModel` или  `FileCodeModel` интерфейс возвращается из объекта  `Project` и  <xref:EnvDTE.ProjectItem> объекты.  Укажите любую функциональность от этого интерфейса, который соответствует вашей системы проектов.  
  
 Если необходимо добавить функции, такие как методы или свойства, которые недоступны из стандарта `CodeModel` и  `FileCodeModel` интерфейсы создайте собственный интерфейс, наследуемый от стандарта.  Убедитесь, что в документ его с системой проекта, поэтому пользователи знают для поиска.  Возвращается стандартный интерфейс, но пользователь может вызвать `QueryInterface` метод или приведение к пользовательскому интерфейсу, если известно, что существует.  
  
## См. также  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)