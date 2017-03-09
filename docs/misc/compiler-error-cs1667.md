---
title: "Ошибка компилятора CS1667 | Microsoft Docs"
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
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1667
Атрибут "атрибут" недопустим в методах доступа свойства или события. Он допустим только в объявлениях "тип\_объявления".  
  
 Эта ошибка возникает при использовании атрибута в методе доступа свойства или события, когда он должен быть в самом свойстве или событии. Эта ошибка может возникать с атрибутами <xref:System.CLSCompliantAttribute>, <xref:System.Diagnostics.ConditionalAttribute> и <xref:System.ObsoleteAttribute>.  
  
## Пример  
 В следующем примере возникает ошибка CS1670:  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```