---
title: "Тег комментария XML &quot;returns&quot; недопустим для элемента языка declare sub | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тег комментария XML &quot;returns&quot; недопустим для элемента языка declare sub
Тег комментария XML "returns" недопустим для элемента языка "declare sub". Комментарий XML будет проигнорирован.  
  
 XML\-комментарий для объявления `Declare Sub` не может содержать тег `<`returns`>`.  
  
 **Идентификатор ошибки:** BC42315  
  
### Исправление ошибки  
  
-   Удалите неподдерживаемый тег `<`returns`>`.  
  
## См. также  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML\-теги для комментариев](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Документирование кода с помощью XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)