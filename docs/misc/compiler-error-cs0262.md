---
title: "Ошибка компилятора CS0262 | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0262
Частичные объявления типа "тип" содержат конфликтующие модификаторы уровня доступа  
  
 Эта ошибка возникает, если разделяемый тип имеет несогласованные модификаторы, такие как public, private, protected, internal или abstract. Эти модификаторы должны быть согласованы во всех частичных объявлениях для этого типа. Для получения дополнительной информации см. [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
## Пример  
 В следующем примере происходит ошибка CS0262:  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```