---
title: "Ошибка компилятора CS0074 | Microsoft Docs"
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
  - "CS0074"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0074"
ms.assetid: 9395c532-3934-4553-8e41-042bfe3399ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0074
"событие": абстрактное событие не может иметь инициализатор  
  
 Если [событие](/dotnet/csharp/language-reference/keywords/event) помечено как **абстрактное**, оно не может быть инициализировано. Для получения дополнительной информации см. [События](/dotnet/csharp/programming-guide/events/index).  
  
 В следующем примере возникает ошибка CS0074.  
  
```  
// CS0074.cs delegate void D(); abstract class Test { public abstract event D e = null;   // CS0074 // try the following line instead // public abstract event D e; public static void Main() { } }  
```