---
title: "Метод &quot;&lt;метод&gt;&quot; в данном контексте недоступен, так как является модификатором &quot;&lt;модификатор&gt;&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30389"
  - "bc30389"
helpviewer_keywords: 
  - "BC30389"
ms.assetid: fae58a68-df91-4741-a8c9-f1bb10e166e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &quot;&lt;метод&gt;&quot; в данном контексте недоступен, так как является модификатором &quot;&lt;модификатор&gt;&quot;.
Предпринята попытка обращения к методу, который недоступен в данном контексте, поскольку он объявлен как `Private`. Возможная причина этой ошибки заключается в том, что компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] импортирует все члены класса и не учитывает регистр, поэтому возможен конфликт имен, различающихся только регистром.  
  
 **Идентификатор ошибки:** BC30389  
  
### Исправление ошибки  
  
-   Рассмотрим следующее объявление метода `Public`.  
  
-   Если ошибка вызвана конфликтом имен, задайте имена, отличающиеся не только регистром.  
  
## См. также  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)