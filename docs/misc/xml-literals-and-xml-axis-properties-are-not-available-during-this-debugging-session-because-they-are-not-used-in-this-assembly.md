---
title: "Литералы XML и свойства оси XML не доступны во время этого сеанса отладки, так как они не используются в этой сборке | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31196"
  - "bc31196"
helpviewer_keywords: 
  - "BC31196"
ms.assetid: 36be5c92-dd6b-41d4-894a-2bd71d772092
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Литералы XML и свойства оси XML не доступны во время этого сеанса отладки, так как они не используются в этой сборке
На литерал XML или свойство оси XML была сделана ссылка в окне **Контрольные значения** или в окне **Интерпретация** во время сеанса отладки, в котором XML в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] недоступен. Такое происходит в случае со сборкой, не использующей XML в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] либо являющейся сборкой выпуска.  
  
 **Идентификатор ошибки:** BC31196  
  
### Исправление ошибки  
  
-   Начните новый сеанс отладки с использованием отладочной сборки.  
  
## См. также  
 [Отладка приложения в Visual Basic](/dotnet/visual-basic/developing-apps/debugging)   
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Свойства оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)