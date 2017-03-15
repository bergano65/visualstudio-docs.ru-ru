---
title: "Предупреждение компилятора (уровень&#160;1) CS3018 | Microsoft Docs"
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
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS3018
"тип" не может быть помечен как совместимый с CLS, поскольку является членом типа "тип", не совместимого с CLS  
  
 Это предупреждение возникает, когда вложенный класс, атрибуту CLSCompliant которого присвоено значение `true`, объявляется как член класса, который объявлен с атрибутом CLSCompliant, равным `false`. Это недопустимо, так как вложенный класс не может быть совместимым с CLS, если он является членом внешнего класса, несовместимого с CLS. Для устранения этого предупреждения удалите атрибут CLSCompliant из вложенного класса либо измените его значение с `true` на `false`. Дополнительные сведения о совместимости CLS см. в разделах [Написание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3) и [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS3018:  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```