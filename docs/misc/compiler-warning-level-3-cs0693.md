---
title: "Предупреждение компилятора (уровень&#160;3) CS0693 | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;3) CS0693
Параметр типа "параметр типа" и параметр типа из внешнего типа "тип" имеют одинаковые имена  
  
 Эта ошибка происходит, если имеется универсальный член, такой как метод внутри универсального класса. Так как параметр типа метода не обязательно должен быть таким же, как и параметр типа класса, им нельзя дать одинаковые имена. Для получения дополнительной информации см. [Универсальные методы](/dotnet/csharp/programming-guide/generics/generic-methods).  
  
 Чтобы избежать возникновения этой ситуации, используйте другое имя для одного из параметров типа.  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS0693:  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```