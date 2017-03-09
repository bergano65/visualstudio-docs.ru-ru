---
title: "Ошибка компилятора CS1935 | Microsoft Docs"
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
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1935
Не удалось найти реализацию шаблона запроса для исходного типа "тип". "метод" не найден. Возможно, не хватает ссылки на System.Core.dll или директивы using для System.Linq.  
  
 Исходный тип в запросе должен быть `IEnumerable`, `IEnumerable<T>`, производным типом или типом, для которого вы или кто\-то другой реализовал стандартные операторы запроса. Если тип источника — `IEnumerable` или `IEnumerable<T>`, то необходимо добавить ссылку на system.core.dll и директиву `using` для пространства имен System.Linq, чтобы включить методы расширения стандартных операторов запроса в область. Пользовательские реализации стандартных операторов запроса следует включить в область таким же образом с директивой `using` и при необходимости со ссылкой на сборку.  
  
### Исправление ошибки  
  
1.  Добавьте необходимые директивы using и ссылки в проект.  
  
## Пример  
 В приведенном ниже коде возникает ошибка CS1935, так как происходит раскомментирование директивы `using` для System.Linq.  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## См. также  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)