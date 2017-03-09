---
title: "Ошибка компилятора CS0736 | Microsoft Docs"
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
  - "CS0736"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0736"
ms.assetid: 06b14feb-81d5-495f-ab2d-6dc3f5e7216f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0736
"имя типа" не реализует член интерфейса "имя члена". Не удается реализовать член интерфейса "имя метода", поскольку он является статическим.  
  
 Эта ошибка возникает в том случае, если статический метод неявно или явно объявлен в качестве реализации члена интерфейса.  
  
### Исправление ошибки  
  
-   Удалите модификатор [static](/dotnet/csharp/language-reference/keywords/static) из объявления метода.  
  
-   Измените имя метода интерфейса.  
  
-   Переопределите содержащий метод тип, чтобы он не наследовал от этого интерфейса.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0736, потому что метод `Program.testMethod` объявлен с модификатором static:  
  
```  
// cs0736.cs namespace CS0736 { interface ITest { int testMethod(int x); } class Program : ITest // CS0736 { public static int testMethod(int x) { return 0; } // Try the following line instead. // public int testMethod(int x) { return 0; } public static void Main() { } } }  
```  
  
## См. также  
 [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)