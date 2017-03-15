---
title: "Предупреждение компилятора (уровень 2) CS0436 | Microsoft Docs"
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
  - "CS0436"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0436"
ms.assetid: c4135d9d-3511-4bbc-9540-48c2091f869c
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS0436
Тип "тип" в сборке "сборка" конфликтует с импортированным типом "тип2" в сборке "сборка". Используется тип, определенный в сборке "сборка".  
  
 Это предупреждение выдается, когда тип в исходном файле \(file\_2\) конфликтует с импортированным типом в file\_1. Компилятор использует тип из исходного файла.  
  
## Пример  
  
```  
// CS0436_a.cs // compile with: /target:library public class A { public void Test() { System.Console.WriteLine("CS0436_a"); } }  
```  
  
## Пример  
 В следующем примере возникает ошибка CS0436.  
  
```  
// CS0436_b.cs // compile with: /reference:CS0436_a.dll // CS0436 expected public class A { public void Test() { System.Console.WriteLine("CS0436_b"); } } public class Test { public static void Main() { A x = new A(); x.Test(); } }  
```