---
title: "Ошибка компилятора CS0059 | Microsoft Docs"
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
  - "CS0059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0059"
ms.assetid: 25a8624b-7f7b-4487-ba80-413d57f9132b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0059
Несогласованность по доступности: уровень доступности типа параметра "тип" ниже уровня доступности делегата "делегат".  
  
 Тип возврата и все типы, указанные в списке формальных параметров метода, должны быть менее доступны, чем сам метод. Для получения дополнительной информации см. [Модификаторы доступа](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
## Пример  
 В следующем примере возникает ошибка CS0059.  
  
```  
// CS0059.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public delegate void MyClassDel( MyClass myClass);   // CS0059 public class Program { public static void Main() { } }  
```