---
title: "Ошибка компилятора CS0623 | Microsoft Docs"
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
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0623
Инициализаторы массивов могут использоваться только в инициализаторах переменных или полей. Используйте выражение с оператором new.  
  
 Выполнена попытка инициализировать массив путем использования инициализатора массива в контексте, в котором это не разрешено.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0623, так как компилятор интерпретирует \\{4\\} как встроенный инициализатор массива внутри внешнего инициализатора массива:  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## См. также  
 [Массивы](/dotnet/csharp/programming-guide/arrays/index)