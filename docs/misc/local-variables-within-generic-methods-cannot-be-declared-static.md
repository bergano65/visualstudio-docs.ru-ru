---
title: "Локальные переменные в универсальных методах не могут объявляться как Static | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Локальные переменные в универсальных методах не могут объявляться как Static
Локальная переменная в универсальной процедуре объявлена с ключевым словом `Static`.  
  
 Visual Basic и .NET Framework сейчас не поддерживают какие\-либо сочетания статических переменных и универсальных процедур.  
  
 **Идентификатор ошибки:** BC32068  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Static` из объявления переменной.  
  
## См. также  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)   
 [НЕ В СБОРКЕ. Практическое руководство: увеличение срока жизни переменной](http://msdn.microsoft.com/ru-ru/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)