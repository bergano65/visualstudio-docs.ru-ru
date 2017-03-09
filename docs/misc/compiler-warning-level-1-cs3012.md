---
title: "Предупреждение компилятора (уровень&#160;1) CS3012 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS3012
Невозможно задать аргумент CLSCompliant в модуле, который отличается от атрибута CLSCompliant в сборке.  
  
 Чтобы модуль был совместим с общеязыковой спецификацией \(CLS\) через `[module:System.CLCSompliant(true)]`, он должен быть собран с параметром компилятора [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md). Дополнительные сведения о CLS см. в разделе [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Пример  
 В следующем примере при сборке без `/target:module` возникает ошибка CS3012:  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```