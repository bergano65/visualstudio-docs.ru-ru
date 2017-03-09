---
title: "Ошибка MSBuild MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB4132
**MSB4132: не удалось распознать версию набора инструментов "\<версия\>".**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] не удалось найти набор инструментов, соответствующий заданному значению `ToolsVersion`.  
  
### Чтобы исправить эту ошибку  
  
-   Укажите допустимое значение для параметра `ToolsVersion` в теге проекта или в командной строке, когда используется ключ MSBuild **\/ToolsVersion**.  
  
## См. также  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)