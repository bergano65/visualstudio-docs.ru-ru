---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project - параметр Devenv"
  - "проекты развертывания, определение"
  - "Devenv, /project - параметр"
  - "project - параметр Devenv (/project)"
  - "проекты [Visual Studio], построение"
  - "проекты [Visual Studio], очистка"
  - "проекты [Visual Studio], перестроение"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает отдельный проект в заданной конфигурации решения, для которого необходимо выполнить построение, очистку, повторное построение или развертывание.  
  
## Синтаксис  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## Аргументы  
 \/build  
 Выполняет построение проекта, заданного параметром `/project` `ProjName`.  
  
 \/clean  
 Удаляет все промежуточные файлы и выходные каталоги, созданные во время построения.  
  
 \/rebuild  
 Удаляет, затем выполняет построение проекта, заданного параметром `/project` `ProjName`.  
  
 \/deploy  
 Указывает, что после построения или повторного построения выполняется развертывание проекта.  
  
 `SolnConfigName`  
 Обязательный.  Имя конфигурации решения, которая будет применяться для решения с именем `SolutionName`.  
  
 `SolutionName`  
 Обязательный.  Полный путь и имя файла решения.  
  
 \/project `ProjName`  
 Необязательный.  Полный путь и имя файла проекта в решении.  Можно ввести путь к файлу проекта относительно папки `SolutionName`, или отображаемое имя проекта, или полный путь к файлу проекта и его имя.  
  
 \/projectconfig `ProjConfigName`  
 Необязательный.  Имя конфигурации построения проекта, которая будет применена для проекта с именем `/project`.  
  
## Заметки  
  
-   Этот аргумент необходимо использовать как часть команды `devenv /build`, \/`clean`, `/rebuild` или `/deploy`.  
  
-   Строки, содержащие пробелы, должны заключаться в двойные кавычки.  
  
-   Сводные данные для построения, включая ошибки, могут отображаться в окне **Командная строка** или любом другом системном журнале, заданном переключателем `/out`.  
  
## Пример  
 В следующем примере выполняется построение проекта `CSharpConsoleApp` при помощи конфигурации построения `Debug` в конфигурации решения `Debug` `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)