---
title: "Команда Open Solution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution - команда"
  - "Открыть решение - команда"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Команда Open Solution
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открытие существующего решения; при этом закрываются все другие открытые решения.  
  
## Синтаксис  
  
```  
File.OpenSolution filename  
```  
  
## Аргументы  
 `Filename`  
 Обязательный.  Полный путь и имя файла открываемого решения.  
  
 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.  
  
## Заметки  
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода пользователем.  
  
## Пример  
 В этом примере открывается решение Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)