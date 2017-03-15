---
title: "Ошибка MSBuild MSB3126 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3126
**MSB3126. Приложение использует сопоставление файлов, но не отмечено для установки.  Сопоставление файлов нельзя использовать для приложений, которые не устанавливаются, например приложений, размещенных в веб\-браузере.**  
  
 Эта ошибка происходит, когда приложение настраивается для использования сопоставлений файлов, но настройка его режима установки — "Использовать только в Интернете".  Поскольку приложения для использования только в Интернете обычно выполняются в браузере, сопоставления файлов недоступны.  
  
### Чтобы исправить эту ошибку  
  
-   В области **Режим установки и параметры** установите **Приложение будет доступно в автономном режиме \(можно будет запустить из меню "Пуск"\)**.  Дополнительные сведения см. в разделе [Практическое руководство. Задание режима установки ClickOnce: автономного или через Интернет](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md).  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)