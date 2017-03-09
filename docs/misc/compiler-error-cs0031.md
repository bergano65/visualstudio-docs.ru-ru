---
title: "Ошибка компилятора CS0031 | Microsoft Docs"
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
  - "CS0031"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0031"
ms.assetid: 91f11ae9-9143-41f4-8002-5c38c8ee0651
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0031
Постоянное значение "значение" не может быть преобразовано в "тип" \(для переопределения используйте синтаксис "unchecked"\).  
  
 Предпринята попытка назначить значение переменной, тип которой не позволяет хранить значения. Для получения дополнительной информации см. [Типы](/dotnet/csharp/programming-guide/types/index).  
  
 Следующий пример приводит к возникновению ошибки CS0031 в контекстах checked и unchecked:  
  
```  
// CS0031.cs namespace CS0031 { public class a { public static void Main() { int num = (int)2147483648M; //CS0031 // Try using a larger numeric type instead: // long num = (long)2147483648M; //CS0031 const decimal d = -10M; // Decimal literal unchecked { const byte b = (byte)d; // CS0031 // For small values try using a signed byte instead: // const sbyte b = (sbyte)d; } } } }  
```  
  
## См. также  
 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked)