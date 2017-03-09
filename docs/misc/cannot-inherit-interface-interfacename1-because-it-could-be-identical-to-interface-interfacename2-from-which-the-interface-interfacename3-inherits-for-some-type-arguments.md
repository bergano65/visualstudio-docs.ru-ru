---
title: "Невозможно наследовать интерфейс &quot;&lt;имя_интерфейса1&gt;&quot;, поскольку он может быть идентичным интерфейсу &quot;&lt;имя_интерфейса2&gt;&quot;, от которого интерфейс &quot;&lt;имя_интерфейса3&gt;&quot; наследует некоторые аргументы типов | Microsoft Docs"
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
  - "bc32123"
  - "vbc32123"
helpviewer_keywords: 
  - "BC32123"
ms.assetid: 2b8fa1f0-3d43-45c6-99d0-328151479b43
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно наследовать интерфейс &quot;&lt;имя_интерфейса1&gt;&quot;, поскольку он может быть идентичным интерфейсу &quot;&lt;имя_интерфейса2&gt;&quot;, от которого интерфейс &quot;&lt;имя_интерфейса3&gt;&quot; наследует некоторые аргументы типов
Универсальный интерфейс наследует от двух или более универсальных интерфейсов, и два из этих наследований могут конфликтовать для некоторых значений аргументов типов.  
  
 Следующие операторы могут привести к этой ошибке.  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 Если `derivedInterface` создается или реализуется, предоставляя один и тот же тип как для `t1`, так и для `t2`, он должен наследовать две версии `interfaceA` с одинаковыми аргументами типов. Это приведет к неоднозначности определения, к какой версии следует получить доступ.  
  
 **Идентификатор ошибки:** BC32123  
  
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