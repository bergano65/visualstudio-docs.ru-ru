---
title: "Предупреждение компилятора (уровень&#160;1) CS3011 | Microsoft Docs"
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
  - "CS3011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3011"
ms.assetid: e27ce521-0147-488b-b4a1-1b6fb5168661
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS3011
"член": только удовлетворяющие требованиям CLS члены могут быть абстрактными  
  
 Член класса не может одновременно быть [абстрактным](/dotnet/csharp/language-reference/keywords/abstract) и несовместимым со спецификацией CLS. В соответствии со спецификацией CLS все члены класса должны быть реализованы. Дополнительные сведения о CLS\-совместимости см. в разделах [Написание CLS\-совместимого кода](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3) и [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS3011:  
  
```  
// CS3011.cs using System; [assembly:CLSCompliant(true)] public abstract class I { [CLSCompliant(false)] public abstract int M();   // CS3011 // OK [CLSCompliant(false)] public void M2() { } } public class C : I { public override int M() { return 1; } public static void Main() { } }  
```