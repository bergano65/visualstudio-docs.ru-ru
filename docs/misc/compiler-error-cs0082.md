---
title: "Ошибка компилятора CS0082 | Microsoft Docs"
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
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0082
Тип "тип" уже резервирует член "имя" с такими же типами параметров  
  
 Во время компиляции свойства преобразуются в методы с префиксами `get_` или `set_`, стоящими перед идентификаторами. Если определить собственный метод, который конфликтует с именем преобразованного метода, возникает ошибка.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0082:  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Свойства](/dotnet/csharp/programming-guide/classes-and-structs/properties)