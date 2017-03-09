---
title: "Ошибка MSBuild MSB4141 | Microsoft Docs"
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
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB4141
**MSB4141: MSBuildToolsPath не указана для ToolsVersion "\<x.x\>".**  
  
 Определен созданный пользователем набор инструментов, но не указано значение для `MSBuildToolsPath`.  
  
### Чтобы исправить эту ошибку  
  
-   Укажите допустимое значение для параметра `MSBuildToolsPath` при определении пользовательского набора инструментов в реестре или в файле конфигурации [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## См. также  
 [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)