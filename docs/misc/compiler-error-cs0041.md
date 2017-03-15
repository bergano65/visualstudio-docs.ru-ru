---
title: "Ошибка компилятора CS0041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0041
Слишком длинное полное имя "тип" для отладочной информации. Компилируйте без параметра "\/debug".  
  
 Эта ошибка может произойти при использовании параметра компилятора [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). При возникновении этой ошибки попробуйте удалить PDB\-файлы из каталога bin и выполнить компиляцию еще раз. Если таким образом не удастся устранить ошибку, то, возможно, необходимо исправить или переустановить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].