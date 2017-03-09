---
title: "Ошибка компилятора CS1730 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1730
Атрибуты сборки и модуля должны находиться перед всеми остальными элементами в файле, кроме предложений using и описаний внешних псевдонимов.  
  
 Атрибут, применяемый на уровне сборки, не может указываться после определений типов.  
  
### Исправление ошибки  
  
1.  Переместите атрибут в начало файла, но под директивами `using` объявлениями псевдонимов `extern`.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS1730:  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## См. также  
 [Атрибуты](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)