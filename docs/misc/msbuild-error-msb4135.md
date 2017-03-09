---
title: "Ошибка MSBuild MSB4135 | Microsoft Docs"
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
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB4135
**MSB4135: ошибка чтения информации о наборе инструментов из раздела реестра "\<раздел\>" или подраздела. '  \<раздел\>**  
  
 Не удалось прочитать информацию о пользовательском наборе инструментов, определенную в реестре.  
  
### Чтобы исправить эту ошибку  
  
-   Если в реестре определен пользовательский набор инструментов, убедитесь, что использованы допустимый для реестра формат, правильное имя \(`ToolsVersion`\) и правильное значение \(`MSBuildBinPath` или `MSBuildToolsPath`\).  
  
## См. также  
 [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)