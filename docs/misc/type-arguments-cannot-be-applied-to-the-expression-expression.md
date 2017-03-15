---
title: "Аргументы типов нельзя использовать в выражении &quot;&lt;выражение&gt;&quot; | Microsoft Docs"
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
  - "bc32058"
  - "vbc32058"
helpviewer_keywords: 
  - "BC32058"
ms.assetid: c6b9b49c-6fb2-47b8-a8bb-464562d3adfd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргументы типов нельзя использовать в выражении &quot;&lt;выражение&gt;&quot;
Псевдоним импорта определен с помощью предложения [Of](/dotnet/visual-basic/language-reference/statements/of-clause), которое передает аргументы типов в псевдоним импорта.  
  
 Аргументы типов используются для универсальных типов, а универсальными могут быть только классы, структуры, интерфейсы, процедуры и делегаты. Ни пространства имен, ни псевдонимы импорта не могут быть универсальными.  
  
 **Идентификатор ошибки:** BC32058  
  
### Исправление ошибки  
  
-   Удалите предложение `Of` и его аргументы типов из псевдонима импорта.  
  
## См. также  
 [Оператор Imports \(пространство имен .NET и тип\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Ссылки и оператор Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [НЕ В СБОРКЕ. Разрешение ссылки, если у нескольких переменных одинаковые имена](http://msdn.microsoft.com/ru-ru/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)