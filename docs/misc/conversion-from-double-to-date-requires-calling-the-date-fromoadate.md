---
title: "Для преобразования из Double в Date требуется вызов метода Date.FromOADate | Microsoft Docs"
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
  - "vbc30533"
  - "bc30533"
helpviewer_keywords: 
  - "BC30533"
ms.assetid: afcfd115-4614-4b0b-ad09-76af8dba2ed5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для преобразования из Double в Date требуется вызов метода Date.FromOADate
Предпринята попытка привести значение `Date` к значению `Double`, что нельзя выполнить без использования метода <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>.  
  
 **Идентификатор ошибки:** BC30533  
  
### Исправление ошибки  
  
-   Используйте метод <xref:System.DateTime.FromOADate%2A> для преобразования значения.  
  
## См. также  
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)