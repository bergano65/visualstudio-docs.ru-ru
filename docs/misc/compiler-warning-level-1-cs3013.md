---
title: "Предупреждение компилятора (уровень 1) CS3013 | Microsoft Docs"
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
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS3013
Добавленные модули должны быть помечены атрибутом CLSCompliant, чтобы соответствовать этой сборке.  
  
 Модуль, который был скомпилирован с параметром компилятора [\/target: module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md), был добавлен в компиляцию с параметром [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). Однако соответствие модуля спецификации CLS не согласуется с состоянием CLS текущей компиляции.  
  
 Соответствие CLS обозначается атрибутом модуля. Например, атрибут `[module:CLSCompliant(true)]` указывает, что модуль является CLS\-совместимым, а `[module:CLSCompliant(false)]` указывает, что модуль не является CLS\-совместимым. Значение по умолчанию — `[module:CLSCompliant(false)]`. Дополнительные сведения о CLS см. в разделе [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).