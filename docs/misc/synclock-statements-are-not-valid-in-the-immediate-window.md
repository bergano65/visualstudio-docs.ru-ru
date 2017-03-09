---
title: "Операторы SyncLock недопустимы в окне интерпретации | Microsoft Docs"
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
  - "vbc30135"
  - "bc30135"
helpviewer_keywords: 
  - "BC30135"
ms.assetid: 099771a1-5bf4-4c16-8fc3-262926c771df
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы SyncLock недопустимы в окне интерпретации
Оператор `SyncLock` выполняет синхронизацию потоков и является недопустимым в контексте отладки.  
  
 **Идентификатор ошибки:** BC30135  
  
### Исправление ошибки  
  
-   Не используйте оператор `SyncLock` в окне **интерпретации**.  
  
## См. также  
 [Окно интерпретации](../ide/reference/immediate-window.md)   
 [Оператор SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)