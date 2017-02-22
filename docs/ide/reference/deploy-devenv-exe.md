---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy - параметр Devenv"
  - "deploy - параметр Devenv"
  - "развертывание приложений [Visual Studio], после построения"
  - "Devenv, /deploy - параметр"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Развертывание решения после построения или повторного построения.  Применяется только к проектам с управляемым кодом.  
  
## Синтаксис  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## Аргументы  
 `SolnConfigName`  
 Обязательный.  Имя конфигурации решения, которая будет использоваться для построений решения с именем `SolutionName`.  
  
 `SolutionName`  
 Обязательный.  Полный путь и имя файла решения.  
  
 \/project `ProjName`  
 Необязательный.  Полный путь и имя файла проекта в решении.  Можно ввести путь к файлу проекта относительно папки `SolutionName`, или отображаемое имя проекта, или полный путь к файлу проекта и его имя.  
  
 \/projectconfig `ProjConfigName`  
 Необязательный.  Имя конфигурации построения проекта, которая будет использоваться для построения проекта с именем `/project`.  
  
## Заметки  
 Задаваемый проект должен быть проектом развертывания.  Если задаваемый проект не является проектом развертывания, то после построения проекта при его передаче для развертывания происходит сбой с выдачей ошибки.  
  
 Строки, содержащие пробелы, должны заключаться в двойные кавычки.  
  
 Сводные данные для построения, включая ошибки, могут отображаться в окне **Командная строка** или любом другом системном журнале, заданном переключателем `/out`.  
  
## Пример  
 В следующем примере выполняется развертывание проекта `CSharpConsoleApp` при помощи конфигурации построения `Release` в конфигурации решения `Release` `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)