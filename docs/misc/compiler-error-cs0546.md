---
title: "Ошибка компилятора CS0546 | Microsoft Docs"
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
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0546
"метод доступа": переопределение невозможно, так как "свойство" не имеет функции доступа set, доступной для переопределения  
  
 Попытка переопределить один из методов доступа для свойства не удалась, так как метод доступа невозможно переопределить. Это ошибка может возникать в указанных ниже случаях.  
  
-   Свойство базового класса не объявлено как [virtual](/dotnet/csharp/language-reference/keywords/virtual).  
  
-   Свойство базового класса не объявляет метод доступа [get](/dotnet/csharp/language-reference/keywords/get) или [set](/dotnet/csharp/language-reference/keywords/set), который вы пытаетесь переопределить.  
  
 Если вы не хотите переопределять свойство базового класса, то можете использовать ключевое слово [new](/dotnet/csharp/language-reference/keywords/new) перед свойством в производном классе.  
  
 Дополнительные сведения см. в разделе [Использование свойств](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Пример  
 В приведенном ниже примере возникает ошибка CS0546, так как в базовом классе не объявлен метод доступа set для свойства.  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## См. также  
 [Свойства](/dotnet/csharp/programming-guide/classes-and-structs/properties)