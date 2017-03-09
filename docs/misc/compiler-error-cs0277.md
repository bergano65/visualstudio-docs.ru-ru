---
title: "Ошибка компилятора CS0277 | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0277
Класс "класс" не реализует член интерфейса "метод\_доступа" "метод\_доступа\_класса" не является открытым  
  
 Эта ошибка возникает при попытке реализовать свойство интерфейса, но реализация метода доступа свойства в классе не является открытой. Методы, которые реализуют члены интерфейса, должны иметь доступность уровня public. Для устранения ошибки удалите модификатор доступа в методе доступа свойства.  
  
## Пример  
 В следующем примере возникает ошибка CS0277.  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```