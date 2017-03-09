---
title: "Преобразование из &quot;&lt;тип1&gt;&quot; в &quot;&lt;тип2&gt;&quot; не может происходить в константном выражении | Microsoft Docs"
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
  - "bc30060"
  - "vbc30060"
helpviewer_keywords: 
  - "BC30060"
ms.assetid: bea60254-67b6-4881-91d2-47854c4d073c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Преобразование из &quot;&lt;тип1&gt;&quot; в &quot;&lt;тип2&gt;&quot; не может происходить в константном выражении
Выражение инициализации в операторе `Const` оценивается как тип данных, который не может быть преобразован в объявленный тип константы.  
  
 **Идентификатор ошибки:** BC30060  
  
### Исправление ошибки  
  
1.  Инициализируйте константу с помощью выражения типа данных, который можно преобразовать в тип, объявленный для константы.  
  
## См. также  
 [Оператор Const](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)