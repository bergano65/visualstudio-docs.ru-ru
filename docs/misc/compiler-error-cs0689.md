---
title: "Ошибка компилятора CS0689 | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0689
Невозможно произвести от "идентификатор", так как это параметр типа  
  
 Базовые классы и интерфейсы для универсальных классов не могут быть указаны параметром типа. Вместо этого производите их от определенного класса или интерфейса либо от универсального класса, либо включите неизвестный тип в качестве члена.  
  
 В следующем примере возникает ошибка CS0689.  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```