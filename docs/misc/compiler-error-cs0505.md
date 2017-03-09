---
title: "Ошибка компилятора CS0505 | Microsoft Docs"
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
  - "CS0505"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0505"
ms.assetid: e3cb9e33-7338-4869-859b-81d7439f0d23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0505
"член1": невозможно переопределить, так как "член2" не является функцией  
  
 Объявление класса пыталось переопределить не являющийся методом объект в базовом классе. Переопределения должны соответствовать типу члена. Если нужен метод с тем же именем, что и метод в базовом классе, используйте ключевое слово [new](/dotnet/csharp/language-reference/keywords/new) \(а не [override](/dotnet/csharp/language-reference/keywords/override)\) в объявлении метода в базовом классе.  
  
 В следующем примере возникает ошибка CS0505:  
  
```  
// CS0505.cs // compile with: /target:library public class clx { public int i; } public class cly : clx { public override int i() { return 0; }   // CS0505 }  
```