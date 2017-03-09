---
title: "Ошибка компилятора CS0212 | Microsoft Docs"
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
  - "CS0212"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0212"
ms.assetid: 1b8973b8-03c9-42a6-bf61-2e401b89387e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0212
Адрес нефиксированного выражения можно получить только внутри инициализатора оператора fixed.  
  
 Для получения дополнительной информации см. [Небезопасный код и указатели](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 В следующем примере показано, как получить адрес нефиксированного выражения. В следующем примере возникает ошибка CS0212:  
  
```  
// CS0212a.cs // compile with: /unsafe /target:library public class A { public int iField = 5; unsafe public void M() { A a = new A(); int* ptr = &a.iField;   // CS0212 } // OK unsafe public void M2() { A a = new A(); fixed (int* ptr = &a.iField) {} } }  
```  
  
 Следующий пример также приводит к возникновению ошибки CS0212 и показывает, как устранить ошибку:  
  
```  
// CS0212b.cs // compile with: /unsafe /target:library using System; public class MyClass { unsafe public void M() { // Null-terminated ASCII characters in an sbyte array sbyte[] sbArr1 = new sbyte[] { 0x41, 0x42, 0x43, 0x00 }; sbyte* pAsciiUpper = &sbArr1[0];   // CS0212 // To resolve this error, delete the previous line and // uncomment the following code: // fixed (sbyte* pAsciiUpper = sbArr1) // { //    String szAsciiUpper = new String(pAsciiUpper); // } } }  
```