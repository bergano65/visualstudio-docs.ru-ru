---
title: "Символ &quot;&lt;имя_символа&gt;&quot; не соответствует объявленному типу данных &quot;&lt;тип&gt;&quot; | Microsoft Docs"
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
  - "vbc30277"
  - "bc30277"
helpviewer_keywords: 
  - "BC30277"
ms.assetid: 9808f57e-a46c-43f9-b5e7-275794627763
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Символ &quot;&lt;имя_символа&gt;&quot; не соответствует объявленному типу данных &quot;&lt;тип&gt;&quot;
Переменная объявлена с одним типом данных, но на нее ссылается символ несовместимого типа данных, например `K$ = 10`, когда переменная `K` объявлена как `Integer`.  
  
 **Идентификатор ошибки:** BC30277  
  
### Исправление ошибки  
  
-   Измените объявленный тип данных переменной или измените либо удалите символ типа в ссылке.  
  
## См. также  
 [Символы типов](/dotnet/visual-basic/programming-guide/language-features/data-types/type-characters)