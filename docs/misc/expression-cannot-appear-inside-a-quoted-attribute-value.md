---
title: "Выражение не может указываться в значении атрибута, заключенном в кавычки | Microsoft Docs"
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
  - "bc31155"
  - "vbc31155"
helpviewer_keywords: 
  - "BC31155"
ms.assetid: ed3e618e-de94-4e4e-afaf-72b11073fb1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Выражение не может указываться в значении атрибута, заключенном в кавычки
Выражение не может указываться в значении атрибута, заключенном в кавычки. Попробуйте удалить кавычки.  
  
 Внедренное выражение в значении атрибута для XML\-литерала заключается в кавычки.  
  
 **Идентификатор ошибки:** BC31155  
  
### Исправление ошибки  
  
-   Удалите разделяющие кавычки из значения атрибута. Ниже представлен пример такого кода.  
  
    ```vb#  
    ' Generates an error. Dim elem = <outer attr="<%= value %>" /> ' Does not generate an error. Dim elem = <outer attr=<%= value %> />  
    ```  
  
## См. также  
 [Встроенные выражения в XML](/dotnet/visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml)   
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)