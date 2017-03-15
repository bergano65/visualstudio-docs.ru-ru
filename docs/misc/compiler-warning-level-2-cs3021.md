---
title: "Предупреждение компилятора (уровень 2) CS3021 | Microsoft Docs"
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
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS3021
Для "тип" не требуется атрибут CLSCompliant, так как данная сборка не имеет атрибута CLSCompliant  
  
 Это предупреждение возникает, если `[CLSCompliant(false)]`  появляется в классе в сборке, которая не имеет набор атрибутов уровня сборки CLSCompliant, установленный в значение true \(т. е. строку `[assembly: CLSCompliant(true)]`\). Поскольку сборка не объявляет себя CLS\-совместимой, не требуется, чтобы какой\-либо объект в сборке сам себя объявлял несовместимым, поскольку он считается несовместимым. Дополнительные сведения о CLS\-совместимости см. в разделе [Написание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
 Чтобы избавиться от этого предупреждения, удалите атрибут или добавьте атрибут уровня сборки.  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS3021:  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## См. также  
 [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)