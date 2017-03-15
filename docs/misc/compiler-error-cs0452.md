---
title: "Ошибка компилятора CS0452 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0452
Тип "имя\_типа" должен быть ссылочным типом для его использования в качестве параметра "имя\_параметра" в универсальном типе или методе "идентификатор\_универсального\_объекта".  
  
 Эта ошибка возникает при передаче типа значения, такого как `struct` или `int`, в качестве параметра в универсальный тип или метод, имеющий ограничение ссылочного типа.  
  
## Пример  
 Следующий код приводит к ошибке CS0452.  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## См. также  
 [Ограничения параметров типа](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)