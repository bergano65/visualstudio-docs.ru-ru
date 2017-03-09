---
title: "Ошибка MSBuild MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB1011
**Укажите, какой файл проекта или решения использовать, так как в этой папке содержится несколько файлов проектов или решений.**  
  
 Если файл проекта не указан в командной строке, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ищет в текущем рабочем каталоге файл с расширением, которое оканчивается слогом "proj" или "sln", и использует этот файл.  В текущем рабочем каталоге содержится несколько файлов с расширением, которое оканчивается слогом "proj" или "sln".  
  
### Чтобы исправить эту ошибку  
  
1.  Укажите имя файла проекта в командной строке.  Например, вместо команды `msbuild` введите `msbuild myapp.proj`.  
  
## См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)