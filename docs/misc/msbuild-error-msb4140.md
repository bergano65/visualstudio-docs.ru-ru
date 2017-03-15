---
title: "Ошибка MSBuild MSB4140 | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB4140
**MSB4140: значения ToolsVersion по умолчанию не заданы ни в реестре, ни в файле конфигурации.**  
  
 В проекте не указано значение `ToolsVersion` по умолчанию.  Поэтому неизвестно, какое значение должен использовать [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что значение `DefaultToolsVersion` указано либо в реестре, где определяются наборы инструментов, либо в файле конфигурации \(например, в msbuild.exe.config\).  
  
## См. также  
 [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)