---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs - параметр Devenv"
  - "Devenv, /ResetSkipPkgs - параметр"
  - "ResetSkipPkgs - параметр"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Удаляет все параметры пропуска загрузки, добавленные пользователями к пакетам VSPackage для исключения возможных проблем при загрузке пакетов VSPackage, а затем запускает приложение [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Синтаксис  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## Заметки  
 Наличие тега SkipLoading отключает загрузку VSPackage. Удаление этого тега повторно включает загрузку VSPackage.  
  
## Пример  
 В следующем примере выполняется удаление всех тегов SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)