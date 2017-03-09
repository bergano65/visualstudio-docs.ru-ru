---
title: "Невозможно наследовать интерфейс &quot;&lt;interfacename1&gt;&quot;, поскольку он может совпадать с интерфейсом &quot;&lt;interfacename2&gt;&quot; для некоторых аргументов типов. | Microsoft Docs"
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
  - "vbc32120"
  - "bc32120"
helpviewer_keywords: 
  - "BC32120"
ms.assetid: c91f84a1-e61d-4b5f-8028-221e64ac044c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно наследовать интерфейс &quot;&lt;interfacename1&gt;&quot;, поскольку он может совпадать с интерфейсом &quot;&lt;interfacename2&gt;&quot; для некоторых аргументов типов.
Универсальный интерфейс наследует более одного раза от другого универсального интерфейса, и два этих наследования могут конфликтовать для некоторых значений аргументов типов.  
  
 Эта ошибка может быть вызвана указанными ниже операторами.  
  
 `Public Interface interfaceA(Of u)`  
  
 `End Interface`  
  
 `Public Interface derivedInterface(Of t1, t2)`  
  
 `Inherits interfaceA(Of t1), interfaceA(Of t2)`  
  
 `End Interface`  
  
 Если `derivedInterface` создается или реализуется, предоставляя один тип как для `t1`, так и для `t2`, он должен наследовать две версии `interfaceA` с одинаковыми аргументами типов. Это приведет к неоднозначности определения, к какой версии следует получить доступ.  
  
 **Идентификатор ошибки:** BC32120  
  
### Исправление ошибки  
  
-   Измените один из аргументов типов, предоставленных унаследованному интерфейсу, чтобы не было конфликтов.  
  
     \-или\-  
  
-   Удалите из оператора `Inherits` один из интерфейсов, вызывающих возможный конфликт наследования или реализации.  
  
## См. также  
 [НЕ В СБОРКЕ. Общие сведения об интерфейсах](http://msdn.microsoft.com/ru-ru/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)