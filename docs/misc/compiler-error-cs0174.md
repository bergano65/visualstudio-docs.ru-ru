---
title: "Ошибка компилятора CS0174 | Microsoft Docs"
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
  - "CS0174"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0174"
ms.assetid: c34c0fa4-d720-4dc5-b723-014203bab8f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0174
Для ссылки "base" требуется базовый класс.  
  
 Эта ошибка происходит только в том случае, если среда CLR платформы .NET Framework компилирует исходный код для класса `System.Object`, который является единственным классом, не имеющим базового класса.