---
title: "/Log (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Log - параметр Devenv"
  - "Devenv, /Log - параметр"
  - "/Log - параметр [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Регистрирует все действия в файле журнала для устранения неполадок.  Этот файл отображается после вызова `devenv /log` по крайней мере один раз.  Файл журнала по умолчанию:  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Версия*\\ActivityLog.xml,  
  
 где *Версия* — это версия Visual Studio.  Однако можно указать альтернативный путь и имя файла.  
  
## Синтаксис  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## Заметки  
 Этот ключ должен находиться в конце командной строки после всех других параметров.  
  
 Журнал записывается для всех экземпляров Visual Studio, которые были активированы с ключом \/log.  Для экземпляров Visual Studio, которые были активированы без данного ключа, журнал не записывается.  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)