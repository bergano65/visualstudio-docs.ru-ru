---
title: "&quot;&lt;имя_типа&gt;&quot; не может использоваться как атрибут, так как не объявлено как &quot;MustInherit&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31506"
  - "bc31506"
helpviewer_keywords: 
  - "BC31506"
ms.assetid: ea2baf3d-b8e8-4738-9b6d-53409fc4d282
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_типа&gt;&quot; не может использоваться как атрибут, так как не объявлено как &quot;MustInherit&quot;
Классы настраиваемых атрибутов не могут объявляться как `MustInherit`.  
  
 **Идентификатор ошибки:** BC31506  
  
### Исправление ошибки  
  
-   Удалите модификатор `MustInherit` из настраиваемых атрибутов.  
  
## См. также  
 <xref:System.AttributeUsageAttribute>   
 [НЕ В СБОРКЕ. Настраиваемые атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/d72d8a5c-8f64-4614-b15b-cad66845d047)