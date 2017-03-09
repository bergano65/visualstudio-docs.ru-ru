---
title: "Ошибка компилятора CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0726
"спецификатор формата" не является допустимым спецификатором формата  
  
 Эта ошибка возникает в отладчике. При вводе имени переменной в окне отладчика можно через запятую указать спецификатор формата. Например, можно указать `myInt, h` или `myString,nq`. Эта ошибка возникает, если компилятор не распознает [Определители формата в C\#](../debugger/format-specifiers-in-csharp.md).