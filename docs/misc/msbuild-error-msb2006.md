---
title: "Ошибка MSBuild MSB2006 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB2006
**В файле проекта отсутствует корневой элемент \<{0}\>.**  
  
 Имя корневого элемента указано неправильно или не распознается [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Чтобы исправить эту ошибку  
  
-   Проверьте правильность написания имени элемента.  
  
-   Проверьте, не был ли файл проекта изменен или поврежден.  Если он изменен или поврежден, откройте проект в той версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], в которой он был создан, сохраните его и попробуйте преобразовать еще раз.  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)