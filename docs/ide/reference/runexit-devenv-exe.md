---
title: "/Runexit (devenv.exe) | Microsoft Docs"
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
  - "/runexit - параметр Devenv"
  - "Devenv, runexit - параметр"
  - "runexit - параметр Devenv"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Компилирует и выполняет заданный проект или заданное решение, а затем закрывает интегрированную среду разработки \(IDE\).  
  
## Синтаксис  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## Аргументы  
 `SolutionName`  
 Обязательный.  Полный путь и имя файла решения.  
  
 `ProjectName`  
 Обязательный.  Полный путь и имя файла проекта.  
  
## Заметки  
 Компилирует и выполняет заданный проект или заданное решение в соответствии с параметрами, определенными для активной конфигурации решения.  Этот переключатель минимизирует интегрированную среду разработки \(IDE\) во время выполнения проекта или решения и закрывает IDE после завершения выполнения проекта или решения.  
  
-   Строки, содержащие пробелы, должны заключаться в двойные кавычки.  
  
-   Сводные данные, включая ошибки, могут отображаться в окне **Командная строка** или любом другом системном журнале, заданном переключателем `/out`.  
  
## Пример  
 В этом примере выполняется решение `MySolution` в минимизированной интегрированной среде разработки \(IDE\), использующей активную конфигурацию развертывания, а затем IDE закрывается.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)