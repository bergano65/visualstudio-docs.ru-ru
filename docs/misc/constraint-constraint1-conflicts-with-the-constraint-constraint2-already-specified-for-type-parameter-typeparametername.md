---
title: "Ограничение &quot;&lt;ограничение1&gt;&quot; конфликтует с ограничением &quot;&lt;ограничение2&gt;&quot;, которое уже задано для параметра типа &quot;&lt;имя_типа_параметра&gt;&quot; | Microsoft Docs"
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
  - "vbc32119"
  - "bc32119"
helpviewer_keywords: 
  - "BC32119"
ms.assetid: 30e6778d-5c2b-4f2d-a136-4e66fa9fbe4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ограничение &quot;&lt;ограничение1&gt;&quot; конфликтует с ограничением &quot;&lt;ограничение2&gt;&quot;, которое уже задано для параметра типа &quot;&lt;имя_типа_параметра&gt;&quot;
Универсальный тип объявлен с конфликтующими ограничениями в параметре типа.  
  
 Эту ошибку может вызвать следующий оператор.  
  
 `Public Class testClass(Of t As {Structure, Class })`  
  
 Ограничения `Structure` и `Class` вызывают конфликт в параметре типа `t`, так как ограничение `Structure` требует, чтобы соответствующий аргумент типа был типом значения, а ограничение `Class` требует, чтобы он был ссылочного типа.  
  
 **Идентификатор ошибки:** BC32119  
  
### Исправление ошибки  
  
-   Измените ограничения параметра типа во избежание конфликта.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Класс \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)