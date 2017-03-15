---
title: "Ошибка компилятора CS1727 | Microsoft Docs"
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
  - "CS1727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1727"
ms.assetid: 66478a58-e0f6-4886-b940-5473ad485a01
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1727
Автоматическая отправка отчета об ошибке без авторизации невозможна. Пожалуйста, посетите "...", чтобы авторизировать отправку отчета.  
  
 На веб\-сайте, указанном в тексте ошибки, объясняется, как включить автоматические отчеты об ошибках для средств командной строки [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS1727.  
  
```  
// CS1727.cs // compile with: /errorreport:send // CS1727 expected class Test { static void Main(){} }  
```  
  
## См. также  
 [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)