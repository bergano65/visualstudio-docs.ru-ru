---
title: "Ошибка компилятора CS1104 | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1104
Массив параметров не может быть использован с модификатором " this" в методе расширения  
  
 Первый параметр метода расширения не может быть массивом параметров.  
  
### Исправление ошибки  
  
1.  Обратите внимание, что первый параметр определения метода расширения указывает, какой тип метод будет "расширять". Это не входной параметр. Таким образом, в этом месте массив параметров не имеет смысла. Если нужно передать массив параметров, передайте его вторым параметром.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS1104:  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)