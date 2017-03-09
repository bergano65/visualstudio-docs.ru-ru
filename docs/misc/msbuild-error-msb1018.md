---
title: "Ошибка MSBuild MSB1018 | Microsoft Docs"
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
  - "MSBuild.InvalidVerbosityError"
helpviewer_keywords: 
  - "MSB1018"
ms.assetid: fb4deacc-a799-44e8-8980-d70d9da4caa1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1018
**Недопустимый уровень детализации.**  
  
 Указан недопустимый уровень детализации.  
  
### Чтобы исправить эту ошибку  
  
1.  Проверьте правильность написания уровня детализации.  Возможные уровни детализации: q\[uiet\], m\[inimal\], n\[ormal\], d\[etailed\] и diag\[nostic\], например, `/verbosity:quiet`, `/verbosity:q` или `/v:q`  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Средства ведения журнала построения](../msbuild/build-loggers.md)