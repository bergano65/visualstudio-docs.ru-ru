---
title: "Ошибка компилятора CS0447 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0447
Невозможно использовать атрибуты для аргументов\-типов, можно только для параметров\-типов  
  
 Эта ошибка возникает при применении атрибута к аргументу типа, который содержится в операторе вызова. Разрешается применять атрибут к параметру типа в операторе объявления класса или метода, как показано в следующем коде:  
  
```  
class C<[some attribute] T> {…}  
```  
  
 В приведенной ниже строке кода возникает эта ошибка. Предполагается, что класс `C`, определенный в предыдущей строке кода, имеет статический метод с именем `MyStaticMethod`.  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## Пример  
 Приведенный ниже код вызывает ошибку CS0447.  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```