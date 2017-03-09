---
title: "Ошибка компилятора CS1609 | Microsoft Docs"
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
  - "CS1609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1609"
ms.assetid: 89e112f8-6337-4803-8741-2e38497deb8c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1609
Модификаторы нельзя размещать в объявлениях методов доступа к событиям.  
  
 Модификаторы могут размещаться только в объявлениях событий, но не в объявлениях метода доступа события. Для получения дополнительной информации см. [Использование свойств](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Пример  
 В следующем примере возникает ошибка CS1609:  
  
```  
// CS1609.cs // compile with: /target:library delegate int Del(); class A { public event Del MyEvent { private add {}   // CS1609 // try the following line instead // add {} remove {} } }  
```