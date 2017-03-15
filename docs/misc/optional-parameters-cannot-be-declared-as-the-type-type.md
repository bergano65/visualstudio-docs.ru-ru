---
title: "Невозможно объявлять необязательные параметры с типом &quot;&lt;тип&gt;&quot; | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно объявлять необязательные параметры с типом &quot;&lt;тип&gt;&quot;
Необязательные параметры не могут иметь тип данных структуры.  
  
 **Идентификатор ошибки:** BC30423  
  
### Исправление ошибки  
  
1.  Чтобы передать структуру в необязательный параметр, объявите параметр как `Object`.  
  
2.  Используйте функцию `CType` для приведения параметра к этому типу структуры в процедуре.  
  
## См. также  
 [Структуры и классы](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [Функция CType](/dotnet/visual-basic/language-reference/functions/ctype-function)