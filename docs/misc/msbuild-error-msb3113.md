---
title: "Ошибка MSBuild MSB3113 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3113
**MSB3113: не удалось найти файл "\<файл\>".**  
  
 Эта ошибка появляется при обнаружении неразрешимой ссылки во время создания нового манифеста.  Источником ошибки может быть файл проекта или параметр задачи.  
  
### Чтобы исправить эту ошибку  
  
-   Проверьте, не содержит ли файл проектов \(и параметры построения, если выполняется пользовательская сборка\) противоречий в ссылках на файлы.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)