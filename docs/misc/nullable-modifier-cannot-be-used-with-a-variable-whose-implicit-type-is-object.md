---
title: "Модификатор, допускающий значение null, не может использоваться с переменной, неявным типом которой является Object. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Модификатор, допускающий значение null, не может использоваться с переменной, неявным типом которой является Object.
Объявление переменной содержит модификатор типа, допускающий значение null \(?\), но не указывает тип и не выводит тип путем присвоения значения объявленной переменной.  
  
 **Идентификатор ошибки:** BC33112  
  
### Исправление ошибки  
  
-   Укажите тип при объявлении переменной, допускающей значение null. Этот тип не может быть <xref:System.Object>.  
  
-   Присвойте значение при объявлении переменной, допускающей значение null. Тип переменной, допускающей значение null, будет выведен из присвоенного значения. Тип значения не может быть <xref:System.Object>.  
  
## См. также  
 [Типы значения, допускающие Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)