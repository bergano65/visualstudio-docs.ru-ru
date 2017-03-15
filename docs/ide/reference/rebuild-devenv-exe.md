---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild - параметр Devenv"
  - "приложения [Visual Studio], перестроение"
  - "Devenv, /rebuild - параметр"
  - "проекты [Visual Studio], перестроение"
  - "rebuild - параметр Devenv (/rebuild)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Удаляет и затем выполняет построение заданной конфигурации решения.  
  
## Синтаксис  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## Аргументы  
 `SolnConfigName`  
 Обязательное.  Имя конфигурации решения, которая будет использоваться для повторного построения решения с именем `SolutionName`.  
  
 `SolutionName`  
 Обязательное.  Полный путь и имя файла решения.  
  
 \/project `ProjName`  
 Необязательный параметр.  Полный путь и имя файла проекта в решении.  Можно ввести путь к файлу проекта относительно папки `SolutionName`, или отображаемое имя проекта, или полный путь к файлу проекта и его имя.  
  
 \/projectconfig `ProjConfigName`  
 Необязательный параметр.  Имя конфигурации построения проекта, которая будет использоваться для повторного построения проекта с именем `/project`.  
  
## Заметки  
  
-   С помощью этого переключателя выполняется та же функция, что и при помощи команды меню **Перестроить решение** в интегрированной среде разработки \(IDE\).  
  
-   Строки, содержащие пробелы, должны заключаться в двойные кавычки.  
  
-   Сводные данные для удаления и построения, включая ошибки, могут отображаться в окне **Командная строка** или любом другом системном журнале, заданном переключателем `/out`.  
  
## Пример  
 В следующем примере выполняется удаление и повторное построение проекта `CSharpWinApp` при помощи конфигурации построения `Debug` в конфигурации решения `Debug` `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)