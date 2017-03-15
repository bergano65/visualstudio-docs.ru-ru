---
title: "Ограничение &quot;New&quot; нельзя указывать несколько раз для одного параметра типа. | Microsoft Docs"
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
  - "vbc32081"
  - "BC32081"
helpviewer_keywords: 
  - "BC32081"
ms.assetid: afcb30da-3973-4452-9cf3-c027f9866589
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ограничение &quot;New&quot; нельзя указывать несколько раз для одного параметра типа.
Список ограничений включает ограничение [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator) несколько раз.  
  
 Список ограничений для параметра типа может указывать, что аргумент типа, переданный параметру типа, должен предоставлять конструктор без параметров, к которому имеет доступ, создающий код. Тип не может иметь более одного конструктора без параметров, и это требование нельзя указать более одного раза.  
  
 **Идентификатор ошибки:** BC32081  
  
### Исправление ошибки  
  
-   Удалите все избыточные ключевые слова `New`. В списке ограничений должно быть только одно ключевое слово.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)