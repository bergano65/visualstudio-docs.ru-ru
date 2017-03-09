---
title: "Ошибка компилятора CS0250 | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0250
Не вызывайте метод Finalize базового класса напрямую. Он вызывается автоматически из деструктора.  
  
 Программа не может принудительно выполнить очистку ресурсов базового класса.  
  
 Дополнительные сведения см. в разделе [Методы Finalize и деструкторы](http://msdn.microsoft.com/ru-ru/fd376774-1643-499b-869e-9546a3aeea70).  
  
 Следующий пример приводит к возникновению ошибки CS0250:  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```