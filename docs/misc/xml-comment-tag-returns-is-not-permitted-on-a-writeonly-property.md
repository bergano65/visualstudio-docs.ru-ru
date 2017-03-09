---
title: "Тег комментария XML &quot;returns&quot; недопустим для свойства WriteOnly | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42313"
  - "bc42313"
helpviewer_keywords: 
  - "BC42313"
ms.assetid: 43dca605-187e-4b0b-b29f-5cc4dcdc5f9f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тег комментария XML &quot;returns&quot; недопустим для свойства WriteOnly
Тег комментария XML "returns" недопустим для свойства "WriteOnly". Комментарий XML будет проигнорирован.  
  
 XML\-комментарий для объявления свойства только для записи не может содержать тег \<returns\>.  
  
 **Идентификатор ошибки:** BC42313  
  
### Исправление ошибки  
  
-   Удалите неподдерживаемый тег \<returns\>.  
  
## См. также  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML\-теги для комментариев](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Документирование кода с помощью XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)