---
title: "Ошибка компилятора CS1958 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1958
Выражения инициализатора объекта и коллекции не могут применяться к выражению создания делегата  
  
 В отличие от класса или структуры, делегат не имеет членов, поэтому инициализатору объекта нечего инициализировать. Если эта ошибка возникает, то возможно она вызвана фигурными скобками после выражения создания делегата. Просто удалите эти фигурные скобки, и ошибка исчезнет.  
  
### Исправление ошибки  
  
1.  Удалите фигурные скобки.  
  
## Пример  
 В следующем коде возникает ошибка CS1958.  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```