---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/SafeMode - параметр Devenv"
  - "Devenv, /SafeMode - параметр"
  - "SafeMode - параметр"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в безопасном режиме, загружая только стандартную среду и службы по умолчанию.  
  
## Синтаксис  
  
```  
devenv /SafeMode   
```  
  
## Заметки  
 Этот ключ предотвращает загрузку всех сторонних VSPackages при запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], обеспечивая стабильное выполнение.  
  
## Описание  
 В следующем примере [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается в безопасном режиме.  
  
## Код  
  
```  
Devenv.exe /SafeMode  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)