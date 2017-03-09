---
title: "Ошибка MSBuild MSB3123 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsCountExceedsMaximum"
helpviewer_keywords: 
  - "MSB3123"
ms.assetid: 343aa8a8-9ab9-4dd5-be59-8eccf1f3c012
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3123
**MSB3123. Количество сопоставлений файлов превышает максимальное \<ограничение\>.**  
  
 Для каждого файла разрешается только фиксированное число сопоставленных расширений имени файла.  Эта ошибка происходит при попытке сопоставить больше расширений имени файла, чем разрешено для целевой операционной системы.  
  
### Чтобы исправить эту ошибку  
  
-   Ограничьте количество сопоставлений файла до заданного числа.  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)