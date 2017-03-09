---
title: "Ошибка MSBuild MSB1016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1016
**Укажите уровень детализации сведений.**  
  
 Для ключа **\/verbosity** необходимо указать уровень детализации сведений.  
  
### Чтобы исправить эту ошибку  
  
1.  Укажите уровень детализации в формате `/verbosity:<level>`.  Возможные уровни детализации: q\[uiet\], m\[inimal\], n\[ormal\], d\[etailed\] и diag\[nostic\], например, `/verbosity:quiet`, `/verbosity:q` или `/v:q`  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)