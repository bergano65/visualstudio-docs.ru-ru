---
title: "Ошибка компилятора CS0118 | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0118
"конструктор1\_имя" является "конструктор1", но используется как "конструктор2"  
  
 Компилятор обнаружил ситуацию, когда конструктор используется неправильным образом или в конструкторе выполняется попытка использовать запрещенную операцию. Распространенные примеры:  
  
-   попытка создать экземпляр пространства имен \(вместо класса\);  
  
-   попытка вызвать поле \(вместо метода\);  
  
-   попытка использовать тип в качестве переменной;  
  
-   попытка использовать внешний псевдоним в качестве типа.  
  
 Чтобы устранить эту ошибку, убедитесь, что операция, которую вы выполняете, допустима для данного типа.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0118.  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```