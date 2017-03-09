---
title: "Предупреждение компилятора (уровень&#160;1) CS0809 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS0809
Устаревший член "членA" переопределяет неустаревший член "членB".  
  
 Обычно член, помеченный как устаревший, не должен переопределять член, который не помечен как устаревший. Это предупреждение создается в [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] но не в [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
### Исправление ошибки  
  
1.  Удалите атрибут `Obsolete` из переопределяющего члена или добавьте его в член базового класса.  
  
## Пример  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```