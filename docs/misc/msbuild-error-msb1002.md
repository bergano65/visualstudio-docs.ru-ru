---
title: "Ошибка MSBuild MSB1002 | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1002
**Этот ключ не принимает каких\-либо параметров.**  
  
 Для этого ключа нельзя определить параметры.  Требуется указать только имя ключа, после которого не следует ставить двоеточие.  
  
### Чтобы исправить эту ошибку  
  
-   Введите для этого ключа команду без параметров, то есть вместо команды `msbuild /<switch>:<parameters>` введите `msbuild /<switch>`  
  
-   Удалите двоеточие после имени ключа, то есть вместо команды `msbuild /<switch>:` введите `msbuild /<switch>`  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)