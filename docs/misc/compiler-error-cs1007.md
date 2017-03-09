---
title: "Ошибка компилятора CS1007 | Microsoft Docs"
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
  - "CS1007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1007"
ms.assetid: b56ee2c6-8e79-4b9b-8c59-194bdb22bc3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1007
Метод доступа к свойству уже определен.  
  
 При объявлении [свойства](/dotnet/csharp/programming-guide/classes-and-structs/using-properties) также необходимо объявить его методы доступа. Однако свойство не может иметь несколько методов доступа `get` или несколько методов доступа `set`.  
  
## Пример  
 В следующем примере возникает ошибка CS1007:  
  
```  
// CS1007.cs public class clx { public int MyProperty { get { return 0; } get   // CS1007, this is the second get method { return 0; } } public static void Main() {} }  
```