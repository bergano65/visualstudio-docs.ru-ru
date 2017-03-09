---
title: "Ошибка компилятора CS0061 | Microsoft Docs"
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
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0061
Несогласованность по доступности: доступность базового интерфейса "интерфейс\_1" ниже доступности интерфейса "интерфейс\_2"  
  
 [Открытая](/dotnet/csharp/language-reference/keywords/public) конструкция должна возвращать общедоступный объект.  
  
 Доступность интерфейса не может быть снижена в производном интерфейсе. Дополнительные сведения см. в разделах [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index) и [Модификаторы доступа](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 В следующем примере возникает ошибка CS0061.  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```