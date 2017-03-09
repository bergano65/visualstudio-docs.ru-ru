---
title: "Для преобразования из Date в Double требуется вызов метода Date.ToOADate | Microsoft Docs"
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
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для преобразования из Date в Double требуется вызов метода Date.ToOADate
Предпринята попытка привести значение `Date` к значению `Double`, которое не может выполняться без использования метода <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>.  
  
 **Идентификатор ошибки:** BC30532  
  
### Исправление ошибки  
  
-   Используйте метод <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> для преобразования значения.  
  
## См. также  
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)