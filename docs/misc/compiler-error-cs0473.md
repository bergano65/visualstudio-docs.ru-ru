---
title: "Ошибка компилятора CS0473 | Microsoft Docs"
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
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0473
Реализация явного интерфейса "имя\_метода" соответствует более чем одному членом интерфейса. Фактический выбор конкретного члена интерфейса зависит от реализации. Попробуйте вместо явной реализации использовать неявную реализацию интерфейса.  
  
 В некоторых случаях универсальный метод может получить такую же сигнатуру, что и неуниверсальный метод. Проблема заключается в том, что система метаданных Common Language Infrastructure \(CLI\) никаким способом не может однозначно установить, какой метод привязан к какому слоту. Это определение делается на усмотрение CLI.  
  
> [!NOTE]
>  Эта ошибка возникает в Visual Studio 2008 в тех местах, в которых она не возникала в Visual Studio 2005.  
  
### Исправление ошибки  
  
1.  Удалите явную реализацию и оставьте только неявную реализацию `public int TestMethod(int)` в обоих методах интерфейса.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0473:  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## См. также  
 [Невероятные приключения в программировании](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)