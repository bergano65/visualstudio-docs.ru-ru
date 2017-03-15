---
title: "Невозможно указать локальную переменную &quot;&lt;имя_переменной&gt;&quot; до ее объявления | Microsoft Docs"
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
  - "vbc32000"
  - "bc32000"
helpviewer_keywords: 
  - "BC32000"
ms.assetid: 81e2bbe3-8b8a-4bf7-b344-08489d50ef6e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно указать локальную переменную &quot;&lt;имя_переменной&gt;&quot; до ее объявления
Переменная используется внутри процедуры до ее объявления.  
  
 **Идентификатор ошибки:** BC32000  
  
### Исправление ошибки  
  
-   Переместите объявление так, чтобы оно находилось перед первым обращением к переменной.  
  
## См. также  
 [Объявление переменной](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)