---
title: "Ошибка MSBuild MSB3128 | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3128
**MSB3128. Манифесты ClickOnce не могут быть подписаны, потому что они содержат одну или более нехэшированных ссылок.**  
  
 При публикации приложения, имеющего неподписанный манифест, все файлы должны быть включены в хэш.  
  
### Чтобы исправить эту ошибку  
  
1.  Перейдите на страницу **Публикация конструктора проектов**.  
  
2.  Нажмите кнопку **Файлы приложения**.  
  
3.  Установите для параметра **Хэш** значение **Включить** для всех файлов, которые должны быть опубликованы.  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)