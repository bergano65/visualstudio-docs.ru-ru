---
title: "Предупреждение компилятора (уровень 1) CS3023 | Microsoft Docs"
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
  - "CS3023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3023"
ms.assetid: fd7782f9-f18a-4ce8-843b-95bf19b54317
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS3023
Атрибут CLSCompliant не имеет значения при применении к типам возвращаемых значений.  Попробуйте поместить его в методе.  
  
 Типы возврата функции не проверяются на CLS\-совместимость, поскольку правила CLS\-совместимости применяются к методам и объявлениям типов.  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS3023:  
  
```  
// C3023.cs [assembly:System.CLSCompliant(true)] public class Test { [return:System.CLSCompliant(true)]  // CS3023 // Try this instead: // [method:System.CLSCompliant(true)] public static int Main() { return 0; } }  
```