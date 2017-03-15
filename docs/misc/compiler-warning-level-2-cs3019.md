---
title: "Предупреждение компилятора (уровень 2) CS3019 | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS3019
Проверка на соответствие CLS не будет выполнена для типа "тип", поскольку он не видим за пределами данной сборки.  
  
 Это предупреждение возникает, когда тип или член, имеющий атрибут <xref:System.CLSCompliantAttribute>, не видим из другой сборки. Чтобы устранить эту ошибку, удалите данный атрибут во всех классах или членах, которые не видны из другой сборки, или сделайте этот тип или члены видимыми. Дополнительные сведения о CLS\-совместимости см. в разделе [\<PAVE OVER\> Написание CLS\-совместимого кода](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS3019:  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## См. также  
 [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)