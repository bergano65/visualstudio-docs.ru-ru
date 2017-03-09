---
title: "Ошибка MSBuild MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3120
**MSB3120. Длина расширения для сопоставления файлов "\<расширение\>" превышает максимально допустимую длину \<максимальная длина\>.**  
  
 Число символов в расширении сопоставления файлов не должно превышать указанное число.  
  
### Чтобы исправить эту ошибку  
  
-   Установите для атрибута [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) `extension` значение, число символов в котором не превышает допустимый предел для целевой операционной системы.  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)