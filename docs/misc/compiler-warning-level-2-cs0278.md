---
title: "Предупреждение компилятора (уровень&#160;2) CS0278 | Microsoft Docs"
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
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;2) CS0278
"тип" не реализует шаблон "имя\_шаблона". "имя метода" является неоднозначным с "имя метода".  
  
 Существует несколько инструкций на языке C\#, основывающихся на заданных шаблонах, таких как `foreach` и `using`. Например, `foreach` основывается на классе коллекции, реализующем шаблон "перечисление".  
  
 Ошибка CS0278 может произойти, если компилятору не удается выполнить сопоставление из\-за неоднозначности. Например, шаблон "перечисление" требует, чтобы существовал метод с именем `MoveNext`, и ваш код может содержать два метода `MoveNext`. Компилятор попытается найти интерфейс для использования, но рекомендуется определить и устранить причину неоднозначности.  
  
 Для получения дополнительной информации см. [Практическое руководство. Доступ к классу коллекции с помощью оператора foreach](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0278.  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```