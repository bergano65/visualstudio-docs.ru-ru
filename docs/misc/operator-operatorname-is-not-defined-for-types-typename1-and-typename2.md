---
title: "Оператор &quot;&lt;имя_оператора&gt;&quot; для типов &quot;&lt;имя_типа1&gt;&quot; и &quot;&lt;имя_типа2&gt;&quot; не определен | Microsoft Docs"
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
  - "vbc31080"
  - "bc31080"
helpviewer_keywords: 
  - "BC31080"
ms.assetid: d2f77450-2bf2-4b1e-b95f-dbc7878f2777
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;&lt;имя_оператора&gt;&quot; для типов &quot;&lt;имя_типа1&gt;&quot; и &quot;&lt;имя_типа2&gt;&quot; не определен
Оператор "\<имя\_оператора\>" для типов "\<имя\_типа1\>" и "\<имя\_типа2\>" не определен. Для сравнения двух значений ссылочного типа используйте оператор Is.  
  
 Для указанных типов предпринята попытка использовать оператор недопустимым образом. Эта ошибка может быть вызвана использованием оператора "\=" вместо оператора `Is` для сравнения двух объектов.  
  
 **Идентификатор ошибки:** BC31080  
  
### Исправление ошибки  
  
1.  Для сравнения двух ссылочных типов используйте оператор `Is`.  
  
2.  Для обозначения неравенства используйте оператор `Not` вместе с оператором `Is`. Пример:  
  
     [!code-vb[VbVbalrOOP#89](../misc/codesnippet/VisualBasic/operator-operatorname-is-not-defined-for-types-typename1-and-typename2_1.vb)]  
  
## См. также  
 [Оператор Is](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Оператор \=](/dotnet/visual-basic/language-reference/operators/assignment-operator)   
 [Оператор Not](/dotnet/visual-basic/language-reference/operators/not-operator)