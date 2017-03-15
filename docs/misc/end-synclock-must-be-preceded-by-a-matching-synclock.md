---
title: "Оператору End SyncLock должен предшествовать соответствующий оператор SyncLock | Microsoft Docs"
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
  - "vbc30674"
  - "bc30674"
helpviewer_keywords: 
  - "BC30674"
ms.assetid: 2d473b0b-ca9e-43b5-9bcb-b00766bc90a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End SyncLock должен предшествовать соответствующий оператор SyncLock
Блоки `SyncLock` начинаются с ключевого слова `SyncLock` и заканчиваются конструкцией `End` `SyncLock`.  
  
 **Идентификатор ошибки:** BC30674  
  
### Исправление ошибки  
  
-   Убедитесь, что блок `SyncLock` начинается с оператора `SyncLock`.  
  
## См. также  
 [Оператор SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)