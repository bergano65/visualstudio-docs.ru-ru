---
title: "Оператор &quot; #Region&quot; должен заканчиваться соответствующим оператором &quot; #End Region | Microsoft Docs"
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
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot; #Region&quot; должен заканчиваться соответствующим оператором &quot; #End Region
Используйте директиву `#Region`, чтобы указать блок кода, который можно разворачивать и сворачивать с помощью функции структурирования в редакторе кода [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Начало и конец оператора `#Region` должны находиться в одном блоке кода.  
  
 **Идентификатор ошибки:** BC30681  
  
### Исправление ошибки  
  
1.  Вставьте `#End Region` на соответствующее место в коде после оператора `#Region`.  
  
## См. также  
 [Директива \#Region](/dotnet/visual-basic/language-reference/directives/region-directive)