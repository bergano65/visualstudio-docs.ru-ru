---
title: "Ошибка компилятора CS0123 | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0123
Ни одна перегрузка для метода "метод" не соответствует делегату "делегат".  
  
 Не удалось создать делегат, поскольку не использовалась правильная сигнатура. Экземпляры делегата должны объявляться с такой же сигнатурой, как и в объявлении делегата.  
  
 Чтобы устранить эту ошибку, исправьте либо метод, либо сигнатуру делегата. Для получения дополнительной информации см. [Делегаты](/dotnet/csharp/programming-guide/delegates/index).  
  
 Следующий пример приводит к возникновению ошибки CS0123.  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```