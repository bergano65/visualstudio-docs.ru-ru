---
title: "Ошибка компилятора CS0182 | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0182
Аргументом атрибута должно быть константное выражение, выражение typeof или выражение создания массива того же типа, что и параметр атрибута.  
  
 На типы аргументов, которые можно использовать с атрибутами, накладываются определенные ограничения. Обратите внимание, что, помимо ограничений, указанных в сообщении об ошибке, НЕ ДОПУСКАЕТСЯ использовать в качестве аргументов атрибутов следующие типы:  
  
-   [sbyte](/dotnet/csharp/language-reference/keywords/sbyte)  
  
-   [ushort](/dotnet/csharp/language-reference/keywords/ushort)  
  
-   [uint](/dotnet/csharp/language-reference/keywords/uint)  
  
-   [ulong](/dotnet/csharp/language-reference/keywords/ulong)  
  
-   [decimal](/dotnet/csharp/language-reference/keywords/decimal)  
  
 Дополнительные сведения см. в разделе [НЕ В СБОРКЕ. Глобальные атрибуты \(руководство по программированию на C\#\)](http://msdn.microsoft.com/ru-ru/7c6c41f8-f0d5-4345-8987-3d91f9bae136).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0182:  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```