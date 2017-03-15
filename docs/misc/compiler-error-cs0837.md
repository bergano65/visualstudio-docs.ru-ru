---
title: "Ошибка компилятора CS0837 | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0837
Первый операнд оператора is или as не может быть лямбда\-выражением или анонимным методом.  
  
 Лямбда\-выражения и анонимные методы не могут использоваться слева от [is](/dotnet/csharp/language-reference/keywords/is) или [as](/dotnet/csharp/language-reference/keywords/as).  
  
### Исправление ошибки  
  
-   Если ошибка включает оператор `is`, учтите, что `is` принимает значение и тип и пытается преобразовать значение к этому типу с помощью ссылки, упаковки\-преобразования или распаковки\-преобразования. Так как лямбда\-выражения не являются значениями и к ним неприменимы ссылки, упаковки\-преобразования и распаковки\-преобразования, лямбда\-выражения не являются кандидатами для `is`.  
  
-   Если код неправильно использует `as`, исправьте его для правильного выполнения приведения.  
  
## Пример  
 Следующий пример приводит к возникновению ошибок CS0837:  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```