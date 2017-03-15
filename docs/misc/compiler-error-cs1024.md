---
title: "Ошибка компилятора CS1024 | Microsoft Docs"
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
  - "CS1024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1024"
ms.assetid: 41f587cb-1958-4eb6-9f8d-c03500e55e21
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1024
Требуется директива препроцессора.  
  
 Строка начинается с символа "\#", но последующая часть строки не является допустимой [директивой препроцессора](/dotnet/csharp/language-reference/preprocessor-directives/index).  
  
 Следующий пример приводит к возникновению ошибки CS1024:  
  
```  
// CS1024.cs #import System   // CS1024  
```