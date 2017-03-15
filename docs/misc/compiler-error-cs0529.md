---
title: "Ошибка компилятора CS0529 | Microsoft Docs"
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
  - "CS0529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0529"
ms.assetid: 61de8086-f991-455c-b009-bb8cd05f34bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0529
Наследуемый интерфейс "интерфейс1" образует циклическую ссылку в иерархии интерфейсов "интерфейс2".  
  
 Список наследования для [интерфейса](/dotnet/csharp/language-reference/keywords/interface) включает прямую или косвенную ссылку на самого себя. Интерфейс не может наследовать от самого себя.  
  
 В следующем примере возникает ошибка CS0529:  
  
```  
// CS0529.cs namespace x { public interface a { } public interface b : a, c { } public interface c : b   // CS0529, b inherits from c { } }  
```