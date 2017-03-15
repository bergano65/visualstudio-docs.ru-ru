---
title: "Ошибка MSBuild MSB3121 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationMissingAttribute"
helpviewer_keywords: 
  - "MSB3121"
ms.assetid: c1e83a2a-515f-412d-b8b7-4821e510a923
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3121
**MSB3121. У элемента сопоставления файлов в манифесте приложения отсутствует один или несколько следующих обязательных атрибутов: расширение, описание, идентификатор программы или значок по умолчанию.**  
  
 Параметр [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) должен содержать значения для всех четырех атрибутов.  
  
### Чтобы исправить эту ошибку  
  
-   Установите для каждого атрибута [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) допустимое значение.  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)