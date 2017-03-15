---
title: "Ошибка компилятора CS0314 | Microsoft Docs"
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
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0314
Тип "тип1" не может быть использован как параметр\-тип "имя" в универсальном типе или методе "имя". Нет преобразования\-упаковки или преобразования параметра\-типа из "тип1" в "тип2".  
  
 Если универсальным типом используется ограниченный параметр типа, то новый класс также должен удовлетворять тем же ограничениям.  
  
### Исправление ошибки  
  
1.  В приведенном ниже примере добавьте `where T : ClassConstraint` в класс `B`.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0314:  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## См. также  
 [Ограничения параметров типа](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)