---
title: "Ошибка компилятора CS0012 | Microsoft Docs"
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
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0012
Тип "тип" определен в сборке, которая не используется. Необходимо добавить ссылку на сборку "сборка".  
  
 Не найдено определение ссылочного типа. Это может произойти, если требуемый DLL\-файл не включен в компиляцию. Дополнительные сведения см. в разделах [Add Reference Dialog Box](http://msdn.microsoft.com/ru-ru/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) и [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
 Следующая последовательность компиляций приведет к возникновению ошибки CS0012:  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 Затем:  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 Затем:  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 Вы можете устранить эту ошибку CS0012, выполнив компиляцию с `/reference:cs0012b.dll;cs0012a.dll`, или в Visual Studio, используя [Add Reference Dialog Box](http://msdn.microsoft.com/ru-ru/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) для добавления ссылки на cs0012a.dll в дополнение к cs0012b.dll.