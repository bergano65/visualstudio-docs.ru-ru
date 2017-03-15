---
title: "Ошибка компилятора CS0537 | Microsoft Docs"
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
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0537
Класс System.Object не может иметь базовый класс или реализовывать интерфейс.  
  
 Ошибка CS0537 возникает при повторной сборке библиотек классов <xref:System>, когда <xref:System.Object> является производным от другого класса. Эта ошибка происходит в крайне редких случаях. Если она все же возникла, не выполняйте наследование <xref:System.Object> от класса или интерфейса: это корень всей иерархии классов .NET Framework и поэтому не может быть производным от чего\-либо.