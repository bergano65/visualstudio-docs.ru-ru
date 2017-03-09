---
title: "Ошибка компилятора CS0198 | Microsoft Docs"
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
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0198
Присваивание значений полям статического поля "имя", доступного только для чтения, допускается только в статическом конструкторе или инициализаторе переменных  
  
 Переменная, помеченная модификатором [readonly](/dotnet/csharp/language-reference/keywords/readonly), должна содержать тот же модификатор использования [static](/dotnet/csharp/language-reference/keywords/static), что и конструктор, в котором вы хотите ее инициализировать. Дополнительные сведения см. в разделе [Статические конструкторы](/dotnet/csharp/programming-guide/classes-and-structs/static-constructors).  
  
 В следующем примере возникает ошибка CS0198:  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```