---
title: "Ошибка компилятора CS1110 | Microsoft Docs"
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
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1110
Нельзя использовать модификатор this в первом параметре объявления метода без ссылки на библиотеку System.Core.dll. Добавьте ссылку на System.Core.dll или удалите модификатор this из объявления метода.  
  
 Методы расширения поддерживаются в версии 3.5 и более поздних версиях .NET Framework. Методы расширения создают метаданные, помечающие метод атрибутом. Класс атрибута находится в system.core.dll.  
  
### Исправление ошибки  
  
1.  Как говорится в сообщении, добавьте ссылку на System.Core.dll или удалите модификатор `this` из объявления метода.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1110, если файл не компилируется со ссылкой на библиотеку System.Core.dll:  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)