---
title: "VbStrConv.Wide и VbStrConv.Narrow не могут использоваться вместе | Microsoft Docs"
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
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv.Wide и VbStrConv.Narrow не могут использоваться вместе
Приложение пытается объединить взаимоисключающие элементы `Wide` и `Narrow` перечисления `VbStrConv`.  
  
### Исправление ошибки  
  
1.  Удалите `VbStrConv.Wide` или `VbStrConv.Narrow`.  
  
## См. также  
 <xref:System.Globalization>   
 [НЕ В СБОРКЕ. Перечисление VbStrConv](http://msdn.microsoft.com/ru-ru/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)