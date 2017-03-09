---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
Система работы с проектами не может создать папку проекта.  
  
 Система работы с проектами предпринимает попытку создать все выходные папки непосредственно после открытия проекта.  Ниже приводится список выходных папок, создаваемых системой работы с проектами.  
  
 *папка\_проекта*\\obj\\`configname`  
 Временная выходная папка для каждой конфигурации.  
  
 *папка\_проекта*\\obj\\`configname`\\temp  
 Рабочая область, используемая компилятором.  
  
 *папка\_проекта*\\obj\\`configname`\\temppe  
 Здесь создаются временные сборки, используемые конструкторами во время разработки.  
  
 outputdir  
 Папка, заданная свойством "Output Path".  Дополнительные сведения см. в разделе [Страница "Построение" в конструкторе проектов \(C\#\)](../ide/reference/build-page-project-designer-csharp.md).  
  
 Наиболее распространенной причиной сбоя при создании одной из папок в папке "obj" является превышение ограничения MAX\_PATH для имен папок.  
  
 Менее распространенными причинами являются отказ в разрешении на доступ и нехватка места на диске.  
  
 **Чтобы исправить эту ошибку**  
  
-   Если путь слишком длинный, смените расположение проекта или сократите имя конфигурации проекта.  
  
     При возникновении этой ошибки процесс построения завершается неудачей.  
  
## См. также  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/ru-ru/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)