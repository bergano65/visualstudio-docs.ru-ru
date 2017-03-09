---
title: "Метод не может одновременно иметь параметры ParamArray и Optional | Microsoft Docs"
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
  - "vbc30046"
  - "bc30046"
helpviewer_keywords: 
  - "BC30046"
ms.assetid: 41066df8-c9ee-4f67-9f6c-4f62e3abc7be
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод не может одновременно иметь параметры ParamArray и Optional
Аргумент `ParamArray` автоматически является необязательным и должен быть единственным необязательным аргументом в объявлении процедуры. Все предшествующие аргументы должны быть обязательными.  
  
 **Идентификатор ошибки:** BC30046  
  
### Исправление ошибки  
  
-   Удалите необязательные аргументы из объявления.  
  
## См. также  
 [Массивы параметров](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)