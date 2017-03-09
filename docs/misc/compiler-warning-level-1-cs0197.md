---
title: "Предупреждение компилятора (уровень&#160;1) CS0197 | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS0197
Передача аргумента "аргумент" в качестве параметра с ключевым словом ref или out или получение его адреса может вызвать исключение времени исполнения, поскольку она является полем класса, который упаковывается и маршалируется по ссылке.  
  
 Любой класс, производный прямо или косвенно от <xref:System.MarshalByRefObject>, является классом, маршалируемым по ссылке. Такой класс может быть маршалирован по ссылке между процессами и компьютерами. Таким образом, экземпляры этого класса могут быть прокси\-элементами удаленного взаимодействия. Вы не можете передавать поле прокси\-элемента как [ref](/dotnet/csharp/language-reference/keywords/ref) или [out](/dotnet/csharp/language-reference/keywords/out). Таким образом, невозможно передать поля такого класса как `ref` или `out`, если экземпляр не является [this](/dotnet/csharp/language-reference/keywords/this), который не может быть объектом прокси.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0197.  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```