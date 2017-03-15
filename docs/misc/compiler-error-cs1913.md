---
title: "Ошибка компилятора CS1913 | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1913
Не удается инициализировать член "имя". Он не является полем или свойством  
  
 Инициализаторы объектов можно использовать только для инициализации доступных полей или свойств.  
  
### Исправление ошибки  
  
1.  Инициализируйте член класса в обычном конструкторе или другом методе инициализации.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS1913:  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## См. также  
 [Классы и структуры](/dotnet/csharp/programming-guide/classes-and-structs/index)