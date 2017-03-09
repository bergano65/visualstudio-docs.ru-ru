---
title: "Предупреждение компилятора (уровень&#160;2) CS0279 | Microsoft Docs"
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
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;2) CS0279
Тип "имя\_типа" не реализует шаблон "имя\_шаблона". Метод "имя\_метода" либо статический, либо не являющийся открытым.  
  
 В C\# существует несколько операторов, основывающихся на заданных шаблонах, таких как `foreach` и `using`. Например, `foreach` основывается на классе коллекции, реализующем шаблон перечисления. Эта ошибка возникает, если компилятору не удается выполнить сопоставление из\-за того, что метод объявляется как `static` или не `public`. Методы в шаблонах должны быть экземплярами классов и должны быть открытыми.  
  
## Пример  
 В следующем примере возникает ошибка CS0279:  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```