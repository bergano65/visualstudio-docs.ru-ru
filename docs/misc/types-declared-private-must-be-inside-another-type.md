---
title: "Типы, объявленные как Private, должны находиться внутри другого типа | Microsoft Docs"
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
  - "vbc31089"
  - "bc31089"
helpviewer_keywords: 
  - "BC31089"
ms.assetid: 44ea5fe4-4af6-4cea-a4a5-2cf966df2937
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы, объявленные как Private, должны находиться внутри другого типа
Модификатор `Private` использовался для типа, не находящегося внутри другого типа.  
  
 **Идентификатор ошибки:** BC31089  
  
### Исправление ошибки  
  
1.  Используйте менее строгий модификатор доступа, например `Friend`.  
  
2.  Объявите тип с другим типом.  
  
## См. также  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)