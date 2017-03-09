---
title: "Общие методы не могут быть представлены в COM | Microsoft Docs"
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
  - "vbc30943"
  - "bc30943"
helpviewer_keywords: 
  - "BC30943"
ms.assetid: 0e3bff62-f187-4864-8520-70f6be22e869
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Общие методы не могут быть представлены в COM
Компонент [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], содержащий одну или несколько универсальных процедур, экспортируется в COM\-компонент.  
  
 Модель COM не поддерживает универсальные типы и не может взаимодействовать с ними.  
  
 **Идентификатор ошибки:** BC30943  
  
### Исправление ошибки  
  
-   Удалите универсальные процедуры из компонента [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] или не применяйте их для COM\-взаимодействия.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [COM\-взаимодействие](/dotnet/visual-basic/programming-guide/com-interop/index)