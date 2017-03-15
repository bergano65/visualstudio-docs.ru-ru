---
title: "&quot;System.Runtime.InteropServices.DllImportAttribute&quot; не может применяться к методам &quot;AddHandler&quot;, &quot;RemoveHandler&quot; и &quot;RaiseEvent&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31531"
  - "vbc31531"
helpviewer_keywords: 
  - "BC31531"
ms.assetid: 0ea3a16c-cfe0-4cb5-b740-358679272f8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;System.Runtime.InteropServices.DllImportAttribute&quot; не может применяться к методам &quot;AddHandler&quot;, &quot;RemoveHandler&quot; и &quot;RaiseEvent&quot;
Атрибут `DllImportAttribute` был применен к объявлению метода `AddHandler`, `RemoveHandler` или `RaiseEvent`. Этот атрибут может использоваться только с пустым оператором `Function` или `Sub`.  
  
 **Идентификатор ошибки:** BC31531  
  
### Исправление ошибки  
  
-   Удалите атрибут `DllImportAttribute` из объявления метода.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent](http://msdn.microsoft.com/ru-ru/7f765da0-5491-40b6-9ed5-24c98f9daad9)