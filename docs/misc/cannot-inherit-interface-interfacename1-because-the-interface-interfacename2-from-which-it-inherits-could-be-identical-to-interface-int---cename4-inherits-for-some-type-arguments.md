---
title: "Невозможно наследовать интерфейс &quot;&lt;interfacename1&gt;&quot;, поскольку интерфейс &quot;&lt;interfacename2&gt;&quot;, от которого он наследуется, может совпадать с интерфейсом &quot;&lt;interfacename3&gt;&quot;, от которого интерфейс &quot;&lt;interfacename4&gt;&quot; наследует некоторые аргументы типов. | Microsoft Docs"
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
  - "vbc32122"
  - "bc32122"
helpviewer_keywords: 
  - "BC32122"
ms.assetid: 64a66ec7-0f5f-4804-a92b-9a6279fdfd6d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно наследовать интерфейс &quot;&lt;interfacename1&gt;&quot;, поскольку интерфейс &quot;&lt;interfacename2&gt;&quot;, от которого он наследуется, может совпадать с интерфейсом &quot;&lt;interfacename3&gt;&quot;, от которого интерфейс &quot;&lt;interfacename4&gt;&quot; наследует некоторые аргументы типов.
Универсальный интерфейс наследует от двух или более универсальных интерфейсов, некоторые значения аргументов типов которых могут конфликтовать.  
  
 Эта ошибка может быть вызвана указанными ниже операторами.  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface interfaceY(Of w) Inherits interfaceA(Of w) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceX(Of t1), interfaceY(Of t2) End Interface  
```  
  
 Если `derivedInterface` создается или реализуется, предоставляя один тип как для `t1`, так и для `t2`, он должен наследовать две версии `interfaceA` с одинаковыми аргументами типов. Это приведет к неоднозначности определения, к какой версии следует получить доступ.  
  
 **Идентификатор ошибки:** BC32122  
  
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