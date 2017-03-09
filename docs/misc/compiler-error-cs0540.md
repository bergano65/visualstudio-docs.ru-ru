---
title: "Ошибка компилятора CS0540 | Microsoft Docs"
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
  - "CS0540"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0540"
ms.assetid: 2da2cd4a-0ff1-45ea-bb72-ea078bc95dea
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0540
"член\_интерфейса": вмещающий тип не реализует интерфейс "интерфейс"  
  
 Попытка реализовать член интерфейса в [классе](/dotnet/csharp/language-reference/keywords/class), который не наследует от соответствующего [интерфейса](/dotnet/csharp/language-reference/keywords/interface). Следует удалить реализацию члена интерфейса или добавить интерфейс в список базовых классов класса.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0540.  
  
```  
// CS0540.cs interface I { void m(); } public class Clx { void I.m() {}   // CS0540 } // OK public class Cly : I { void I.m() {} public static void Main() {} }  
```  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0540.  
  
```  
// CS0540_b.cs using System; class C { void IDisposable.Dispose() {}   // CS0540 } class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```