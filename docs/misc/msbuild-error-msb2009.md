---
title: "Ошибка MSBuild MSB2009 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB2009
**Атрибут "\<имя атрибута\>" не является допустимым атрибутом элемента "\<имя элемента\>".**  
  
 Имя атрибута указано неправильно или не распознается [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Чтобы исправить эту ошибку  
  
-   Проверьте правильность написания имени атрибута.  
  
-   Проверьте, не был ли файл проекта изменен или поврежден.  Если он изменен или поврежден, откройте проект в той версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], в которой он был создан, сохраните его и попробуйте преобразовать еще раз.  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)