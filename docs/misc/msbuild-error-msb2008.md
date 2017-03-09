---
title: "Ошибка MSBuild MSB2008 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB2008
**Системе проектов Visual Studio не удается преобразовать проекты "{0}".  Она может использоваться только для преобразования клиентских проектов C\# и VB.**  
  
 С помощью [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] можно преобразовать только допустимые проекты [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
### Чтобы исправить эту ошибку  
  
-   Если используется проект [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], проверьте, не был ли изменен или поврежден файл проекта.  Если он изменен или поврежден, откройте проект в той версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], в которой он был создан, сохраните его и попробуйте преобразовать еще раз.  
  
-   Если проект не является проектом [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], для его преобразования используйте подходящее средство.  
  
## См. также  
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)