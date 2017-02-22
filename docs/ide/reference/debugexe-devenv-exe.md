---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
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
  - "/DebugExe - [devenv.exe]"
  - "DebugExe - параметр"
  - "Devenv, /DebugExe - параметр"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открытие указанного исполняемого файла для отладки.  
  
## Синтаксис  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## Аргументы  
 `ExecutableFile`  
 Обязательный.  Путь и имя файла EXE.  
  
 Если EXE\-файл не найден или не существует, предупреждение или ошибка не отображаются и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается в обычном режиме.  
  
## Заметки  
 Любые строки, следующие за параметром `ExecutableFile`, подставляются в этот файл в качестве аргументов.  
  
## Пример  
 Следующий пример открывает файл `MyApplication.exe` для отладки.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)