---
title: "Предупреждение о соответствии спецификации CLS CLS01501 | Microsoft Docs"
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
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01501
**Ограничение varargs не входит в CLS**  
  
 Ограничение varargs не входит в спецификацию CLS.  Спецификацией предусматривается только стандартное соглашение об управляемых вызовах.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем объявлении функции \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS01501:  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 Устранить предупреждение CLS01501 можно с помощью массива параметров.  Дополнительные сведения см. в разделе [Списки аргументов переменных \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli).