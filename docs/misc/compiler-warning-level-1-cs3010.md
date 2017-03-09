---
title: "Предупреждение компилятора (уровень&#160;1) CS3010 | Microsoft Docs"
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
  - "CS3010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3010"
ms.assetid: d57bd750-df15-4e6a-9579-66de8b276b7e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS3010
"член": удовлетворяющие требованиям CLS интерфейсы должны иметь соответствующие требованиям CLS члены  
  
 В сборке, помеченной как `[assembly:CLCSompliant(true)]`, интерфейс содержит член, помеченный как `[CLCSompliant(false)]`. Удалите один из атрибутов совместимости со спецификацией CLS. Дополнительные сведения о CLS\-совместимости см. в разделах [\<PAVE OVER\> Написание CLS\-совместимого кода](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3) и [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS3010:  
  
```  
// CS3010.cs using System; [assembly:CLSCompliant(true)] public interface I { [CLSCompliant(false)] int M();   // CS3010 } public class C : I { public int M() { return 1; } public static void Main() { } }  
```