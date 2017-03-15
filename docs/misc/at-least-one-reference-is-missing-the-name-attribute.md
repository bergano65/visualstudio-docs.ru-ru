---
title: "At least one reference is missing the &#39;Name&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one reference is missing the &#39;Name&#39; attribute
Каждая ссылка должна иметь свойство **Name**, как показано ниже.  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 Это сообщение об ошибке означает, что свойство **Name** не было найдено как минимум для одной ссылки.  
  
 Эта ошибка часто возникает при редактировании файла проекта вручную.  
  
 **Чтобы исправить эту ошибку**  
  
-   Добавьте ссылку повторно.  
  
     Поврежденные ссылки не будут добавлены в проект.  
  
## См. также  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)