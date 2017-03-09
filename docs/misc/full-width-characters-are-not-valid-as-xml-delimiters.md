---
title: "Полноширинные знаки не могут использоваться в качестве разделителей XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Полноширинные знаки не могут использоваться в качестве разделителей XML
Определен XML\-литерал, включающий полноширинный знак как разделитель. Полноширинные знаки также называют расширенными или многобайтовыми символами.  
  
 **Идентификатор ошибки:** BC31197  
  
### Исправление ошибки  
  
-   Удалите полноширинный знак из определения XML\-литерала и замените его допустимым разделительным знаком ANSI. К допустимым разделительным знакам относятся следующие: `<`, `>`, `=`, `:`, `/`.  
  
## См. также  
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Кодировки в .NET Framework](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)