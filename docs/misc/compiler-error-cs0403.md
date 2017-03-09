---
title: "Ошибка компилятора CS0403 | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0403
Невозможно преобразовать null в параметр типа "имя", поскольку он может быть типом значения, не допускающим значения null. Используйте вместо этого default\("T"\).  
  
 Нельзя присвоить значение NULL неизвестному типу с именем, так как он может быть типом значения, который не допускает значения NULL. Если предполагается, что универсальный класс не будет принимать типы значений, используйте ограничение типа класса. Если он может принимать типы значений, такие как встроенные типы, то можно попробовать заменить присвоение NULL выражением `default(T)`, как показано в приведенном ниже примере.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0403:  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```