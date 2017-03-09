---
title: "Косвенное ограничение &quot;&lt;ограничение1&gt;&quot;, полученное из ограничения параметра типа &quot;&lt;параметр_типа1&gt;&quot;, конфликтует с ограничением &quot;&lt;ограничение2&gt;&quot; | Microsoft Docs"
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
  - "bc32111"
  - "vbc32111"
helpviewer_keywords: 
  - "BC32111"
ms.assetid: b03b5840-5318-4844-b2da-1bca4c28d097
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Косвенное ограничение &quot;&lt;ограничение1&gt;&quot;, полученное из ограничения параметра типа &quot;&lt;параметр_типа1&gt;&quot;, конфликтует с ограничением &quot;&lt;ограничение2&gt;&quot;
Универсальный тип объявлен с конфликтующими ограничениями из\-за сочетания прямых и косвенных ограничений.  
  
 Эту ошибку может вызвать следующий оператор.  
  
 `Public Class testClass(Of t1 As {t2, Class}, t2 As Structure)`  
  
 Прямое ограничение `Structure` и косвенное ограничение `Class` приводят к конфликту в параметре типа `t1`, так как ограничение `Structure` требует, чтобы соответствующий аргумент типа был типом значения, а `Class` требует, чтобы он был ссылочного типа.  
  
 **Идентификатор ошибки:** BC32111  
  
### Исправление ошибки  
  
-   Измените ограничения параметра типа во избежание конфликта ограничений.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Класс \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)