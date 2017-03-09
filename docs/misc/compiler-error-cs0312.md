---
title: "Ошибка компилятора CS0312 | Microsoft Docs"
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
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0312
Тип "тип1" не может быть использован как параметр типа "имя" в универсальном типе или методе "имя". Допускающий значение null тип "тип1" не удовлетворяет ограничению типа "тип2".  
  
 Допускающий значение null тип отличается от своего аналога, не допускающего значение null; между ними не существует неявное преобразование ссылок или преобразование удостоверений. Допускающая значения null упаковка\-преобразование не удовлетворяет ограничению универсального типа. В следующем примере первый параметр типа является `Nullable<int>`, а второй параметр типа является `System.Int32`.  
  
### Исправление ошибки  
  
1.  Удалите ограничение.  
  
2.  В следующем примере сделайте второй аргумент типа либо `int?`, либо `object`.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0312:  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 Хотя допускающий значения null тип отличается от типа, не допускающего значения null, между ними разрешены различные виды преобразований.  
  
## См. также  
 [Типы, допускающие значения NULL](/dotnet/csharp/programming-guide/nullable-types/index)