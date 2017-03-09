---
title: "Ошибка компилятора CS0453 | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0453
Для использования в качестве параметра "имя параметра" в универсальном типе или методе "идентификатор" тип "имя типа" должен быть типом значения, не допускающим значения NULL  
  
 Эта ошибка возникает при использовании аргумента, который не принадлежит к типу значения, для создания экземпляра универсального типа или метода, имеющего ограничение **value**. Она также может происходить, если используется аргумент, принадлежащий к типу значения, который допускает значение NULL. См. две последние строки кода в представленном ниже примере.  
  
## Пример  
 Приведенный ниже код вызывает эту ошибку.  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```