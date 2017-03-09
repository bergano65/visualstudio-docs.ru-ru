---
title: "Ошибка компилятора CS1918 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1918
Членам свойства "имя" типа "тип" не могут быть присвоены значения с помощью инициализатора объекта, поскольку они имеют тип значения  
  
 Эта ошибка возникает при попытке использовать инициализатор объекта для инициализации свойств структуры, которая сама является свойством инициализируемого класса.  
  
### Исправление ошибки  
  
1.  Если в инициализаторе объекта необходимо полностью инициализировать поля свойства, измените структуру на класс. В противном случае после создания объекта с помощью инициализатора объекта инициализируйте члены структуры в вызове отдельного метода.  
  
## Пример  
 В следующем примере возникает ошибка CS1918:  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## См. также  
 [Инициализаторы объектов и коллекций](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)