---
title: "Практическое руководство. Замена параметров в шаблоне | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметры шаблонов, замещение"
  - "шаблоны Visual Studio, использование параметров"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Замена параметров в шаблоне
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Вы можете заменить параметры шаблона, такие как имена классов и пространства имен, при создании файла на основе шаблона.  Полный список параметров шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
## Процедура  
 Параметры в файлах шаблона можно заменить при создании проекта на основе этого шаблона.  Здесь описывается, как создать шаблон, который заменяет имя пространства имен на безопасное имя проекта при создании нового проекта с помощью шаблона.  
  
#### Использование параметра для замены имени пространства имен именем проекта  
  
1.  Вставьте параметр в один или несколько файлов кода в шаблоне.  Пример:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Параметры шаблона записываются в формате $*параметр*$.  
  
2.  В VSTEMPLATE\-файле шаблона найдите элемент `ProjectItem`, содержащий этот файл.  
  
3.  Задайте для атрибута `ReplaceParameters` элемента `ProjectItem` значение `true`.  Пример:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## См. также  
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Элемент ProjectItem \(шаблоны элементов Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)