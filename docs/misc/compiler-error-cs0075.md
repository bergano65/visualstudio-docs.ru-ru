---
title: "Ошибка компилятора CS0075 | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0075
Для приведения отрицательного значения следует заключить значение в круглые скобки  
  
 Если выполняется приведение с помощью ключевого слова, идентифицирующего предопределенный тип, то скобки не требуются. В противном случае необходимо использовать скобки, так как \(x\) –y не будет считаться выражением приведения. Из спецификации C\#, раздел 7.6.6:  
  
 *Из правила устранения неоднозначности следует, что если x и y являются идентификаторами, \(x\)y \(x\)\(y\) и \(x\)\(\-y\) являются выражениями приведения, но \(x\) –y — нет, даже если x обозначает тип. Однако если x является ключевым словом, идентифицирующим предопределенный тип \(например int\), все четыре формы являются выражениями приведения \(поскольку такое ключевое слово не может быть выражением само по себе\).*  
  
 Следующий код приводит к возникновению ошибки CS0075:  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## См. также  
 [Приведение и преобразование типов](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)