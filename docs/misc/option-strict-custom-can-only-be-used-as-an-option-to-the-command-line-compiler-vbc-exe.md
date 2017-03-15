---
title: "Option Strict Custom может использоваться только как параметр компилятора командной строки (vbc.exe). | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict Custom может использоваться только как параметр компилятора командной строки (vbc.exe).
Оператор `Option Strict` принимает в качестве аргументов только `On` и `Off`; `Option Strict Custom` не допускается.  
  
 Используйте параметр компилятора `/optionstrict:custom`, чтобы предупреждать, когда не накладывается ограничение на строгую семантику языка.  
  
 **Идентификатор ошибки:** BC31141  
  
### Исправление ошибки  
  
1.  Удалите `Option Strict Custom` из исходного кода.  
  
2.  Укажите параметр `/optionstrict:custom`. Для получения дополнительной информации см. [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
## См. также  
 [Оператор Option \<ключевое\_слово\>](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)