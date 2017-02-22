---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean - параметр Devenv"
  - "построения [Team System], очистка файлов"
  - "clean - параметр Devenv"
  - "Devenv, /clean - параметр"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Удаление всех промежуточных файлов и выходных каталогов.  
  
## Синтаксис  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## Аргументы  
 `FileName`  
 Обязательный.  Полный путь и имя файла решения или проекта.  
  
 \/project `ProjName`  
 Необязательный.  Полный путь и имя файла проекта в решении.  Можно ввести путь к файлу проекта относительно папки `SolutionName`, или отображаемое имя проекта, или полный путь к файлу проекта и его имя.  
  
 \/projectconfig `ProjConfigName`  
 Необязательный.  Имя конфигурации построения проекта, которая будет использоваться для удаления проекта с именем `/project`.  
  
## Заметки  
 С помощью этого переключателя выполняется та же функция, что и при помощи команды меню **Удалить решение** в интегрированной среде разработки \(IDE\).  
  
 Строки, содержащие пробелы, должны заключаться в двойные кавычки.  
  
 Сводные данные для удаления и построения, включая ошибки, могут отображаться в окне **Командная строка** или любом другом системном журнале, заданном переключателем `/out`.  
  
## Пример  
 В первом примере решение `MySolution` очищается с помощью конфигурации по умолчанию, заданной в файле решения.  
  
 Во втором примере выполняется удаление проекта `CSharpConsoleApp` при помощи конфигурации построения `Debug` в конфигурации `Debug` решения `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)