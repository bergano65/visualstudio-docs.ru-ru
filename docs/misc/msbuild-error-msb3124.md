---
title: "Ошибка MSBuild MSB3124 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3124
**MSB3124. Для расширения "\<имя расширения\>" уже создано сопоставление файлов.**  
  
 Эта ошибка происходит, когда встречается дублированное расширение сопоставления файлов.  
  
### Чтобы исправить эту ошибку  
  
-   Удалите атрибуты [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) `extension`, не являющиеся уникальными.  Все имеющиеся в списке атрибуты расширения элемента \<fileAssociation\> должны быть уникальными.  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)