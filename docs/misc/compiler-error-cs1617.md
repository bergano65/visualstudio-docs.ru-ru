---
title: "Ошибка компилятора CS1617 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1617
Недопустимый параметр "параметр" для \/langversion; должно быть задано значение ISO\-1, ISO\-2 или Default  
  
 Эта ошибка возникает, если вы использовали параметр командной строки или параметр проекта [\/langversion](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option), но не указали параметр допустимого языка. Чтобы устранить эту ошибку, проверьте синтаксис командной строки или параметр проекта и измените его на один из приведенных вариантов.  
  
 Например, компиляция с `csc /langversion:ISO` приведет к возникновению ошибки CS1617.