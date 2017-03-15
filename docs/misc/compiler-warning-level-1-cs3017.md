---
title: "Предупреждение компилятора (уровень&#160;1) CS3017 | Microsoft Docs"
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
  - "CS3017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3017"
ms.assetid: 8e56b2f0-9caf-4c9a-98c2-d3ad0b70e767
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS3017
Невозможно задать аргумент CLSCompliant в модуле, который отличается от атрибута CLSCompliant в сборке.  
  
 Это предупреждение возникает при наличии атрибута CLSCompliant сборки, который конфликтует с атрибутом CLSCompliant модуля. В CLS\-совместимой сборке не могут содержаться модули, не являющиеся CLS\-совместимыми. Чтобы устранить это предупреждение, убедитесь, что оба атрибута CLSCompliant сборки и модуля имеют значение true или false, или удалите один из атрибутов. Дополнительные сведения о CLS\-совместимости см. в разделах [Написание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3) и [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Пример  
 В следующем примере возникает ошибка CS3017:  
  
```  
// CS3017.cs // compile with: /target:module using System; [module: CLSCompliant(true)] [assembly: CLSCompliant(false)]  // CS3017 // Try this line instead: // [assembly: CLSCompliant(true)] class C { static void Main() {} }  
```