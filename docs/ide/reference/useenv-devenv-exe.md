---
title: "/UseEnv (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.UseEnvVars.ExcludePath"
  - "VC.Project.UseEnvVars.LibraryPath"
  - "VC.Project.UseEnvVars.SourcePath"
  - "VC.Project.UseEnvVars.Include"
  - "VC.Project.UseEnvVars.Path"
  - "VC.Project.UseEnvVars.ReferencePath"
helpviewer_keywords: 
  - "/UseEnv - параметр Devenv"
  - "Devenv, /UseEnv"
  - "UseEnv - параметр"
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /UseEnv (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Запускается приложение [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], и загружаются переменные среды в диалоговом окне **Каталоги VC\+\+**.  
  
## Синтаксис  
  
```  
Devenv /useenv  
```  
  
## Пример  
 В приведенном ниже примере выполняется запуск приложения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и загрузка переменных среды в диалоговом окне **Каталоги VC\+\+**.  
  
```  
Devenv.exe /useenv  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)