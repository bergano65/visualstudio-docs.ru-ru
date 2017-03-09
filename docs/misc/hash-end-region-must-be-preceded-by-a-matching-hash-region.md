---
title: "Оператору #End Region должен предшествовать соответствующий оператор #Region. | Microsoft Docs"
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
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору #End Region должен предшествовать соответствующий оператор #Region.
С помощью `#Region` вы можете указать блок кода, который можно разворачивать и сворачивать при использовании функции структурирования редактора кода [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Начало и конец операторов `#Region` должны находиться в одном блоке кода.  
  
 **Идентификатор ошибки**: BC30680  
  
### Исправление ошибки  
  
-   Вставьте `#Region` в нужное место до соответствующего оператора `#End` `Region`.  
  
## См. также  
 [Директива \#Region](/dotnet/visual-basic/language-reference/directives/region-directive)