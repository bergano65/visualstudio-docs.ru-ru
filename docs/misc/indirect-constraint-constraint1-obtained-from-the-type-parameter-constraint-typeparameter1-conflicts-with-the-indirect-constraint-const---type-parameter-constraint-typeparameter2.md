---
title: "Косвенное ограничение &quot;&lt;ограничение1&gt;&quot;, полученное от ограничения параметра типа &quot;&lt;параметр_типа1&gt;&quot;, конфликтует с косвенным ограничением &quot;&lt;ограничение2&gt;&quot;, полученным от ограничения параметра типа &quot;&lt;параметр_типа2&gt;&quot; | Microsoft Docs"
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
  - "bc32109"
  - "vbc32109"
helpviewer_keywords: 
  - "BC32109"
ms.assetid: 37abd3b4-25dc-4959-8617-ce93a02bbf47
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Косвенное ограничение &quot;&lt;ограничение1&gt;&quot;, полученное от ограничения параметра типа &quot;&lt;параметр_типа1&gt;&quot;, конфликтует с косвенным ограничением &quot;&lt;ограничение2&gt;&quot;, полученным от ограничения параметра типа &quot;&lt;параметр_типа2&gt;&quot;
Универсальный тип объявлен с конфликтующими ограничениями из\-за сочетания косвенных ограничений.  
  
 Эту ошибку может вызвать следующий оператор:  
  
```  
Public Class testClass(Of t1 As {t2, t3}, t2 As Structure, t3 As Class)  
```  
  
 Косвенные ограничения `Structure` и `Class` вызывают конфликт для параметра типа `t1`, так как ограничение `Structure` требует, чтобы аргумент соответствующего типа был типом значения, а `Class` требует ссылочного типа.  
  
 **Идентификатор ошибки:** BC32109  
  
### Исправление ошибки  
  
-   Измените ограничения на параметры типа во избежание конфликта ограничений.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Класс \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)