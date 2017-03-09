---
title: "/Command (devenv.exe) | Microsoft Docs"
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
  - "/command - параметр Devenv"
  - "Devenv, /command - параметр"
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Command (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Выполняет заданную команду после запуска интегрированной среды разработки \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Синтаксис  
  
```  
devenv /command CommandName  
```  
  
## Аргументы  
 `CommandName`  
 Обязательный.  Полное имя команды [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] или ее псевдоним в двойных кавычках.  Дополнительные сведения о команды и синтаксис псевдонима см. в разделе [Команды Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## Заметки  
 После завершения запуска в интегрированной среде разработки \(IDE\) выполняется команда с указанным именем.  Если используется этот переключатель, то при запуске IDE домашняя страница [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не отображается.  
  
 Если надстройка предоставляет команду, этот переключатель может использоваться для запуска надстройки из командной строки.  Для получения дополнительной информации см. [Практическое руководство. Управление надстройками с помощью диспетчера надстроек](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md).  
  
## Пример  
 В приведенном примере запускается приложение [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], и автоматически выполняется макрос Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)