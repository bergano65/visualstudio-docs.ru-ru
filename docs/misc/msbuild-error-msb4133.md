---
title: "Ошибка MSBuild MSB4133 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB4133
**MSB4133: указана версия набора инструментов по умолчанию "\<x.x.\>", но ее определение найти не удалось.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] не удается найти набор инструментов, определенный в файле проекта как `DefaultToolsVersion`.  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что значение `DefaultToolsVersion` указано правильно и что этот набор инструментов определен либо в реестре, либо в файле конфигурации [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## См. также  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)