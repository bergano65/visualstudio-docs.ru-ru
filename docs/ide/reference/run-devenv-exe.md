---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r - параметр Devenv"
  - "/run - Devenv"
  - "приложения [Visual Studio], выполнение"
  - "Devenv, run - параметр"
  - "r - параметр Devenv (/r)"
  - "run - параметр Devenv"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Компилирует и выполняет указанный проект или решение.  
  
## Синтаксис  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## Аргументы  
 `SolutionName`  
 Обязательный.  Полный путь и имя файла решения.  
  
 `ProjectName`  
 Обязательный.  Полный путь и имя файла проекта.  
  
## Заметки  
 Компилирует и выполняет заданный проект или заданное решение в соответствии с параметрами, определенными для активной конфигурации решения.  С помощью этого переключателя запускается интегрированная среда разработки \(IDE\), которая остается активной после завершения выполнения проекта или решения.  
  
-   Строки, содержащие пробелы, должны заключаться в двойные кавычки.  
  
-   Сводные данные, включая ошибки, могут отображаться в окне **Командная строка** или любом другом системном журнале, заданном переключателем `/out`.  
  
## Пример  
 В этом примере выполняется решение `MySolution` с использованием активной конфигурации развертывания.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)