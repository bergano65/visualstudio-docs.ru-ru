---
title: "Ошибка компилятора CS0058 | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0058
Несогласованность по доступности: тип возврата "тип" менее доступен, чем делегат "делегат"  
  
 Открытая конструкция должна возвращать общедоступный объект. Для получения дополнительной информации см. [Модификаторы доступа](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 В следующем примере возникает ошибка CS0058, поскольку никакой модификатор доступа не применяется к MyClass и, таким образом, ему присваивается закрытый доступ по умолчанию:  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## См. также  
 [закрытый](/dotnet/csharp/language-reference/keywords/private)