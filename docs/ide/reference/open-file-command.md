---
title: "Команда Open File | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile - команда"
  - "команды"
  - "Открыть файл - команда"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Команда Open File
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открытие существующего файла и указание редактора.  
  
## Синтаксис  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## Аргументы  
 `filename`  
 Обязательный.  Полный или частичный путь и имя открываемого файла.  Пути, которые содержат пробелы, необходимо заключать в кавычки.  
  
## Переключатели  
 \/e:`editorname`  
 Необязательный.  Имя редактора, в котором будет открыт файл.  Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 \/e: синтаксис аргумента`editorname` используются имена в редакторе по мере их появления в диалоговое окно открыть с помощью ", заключенные в кавычки.  
  
 Например, чтобы открыть файл в редакторе исходного кода, необходимо ввести для аргумента \/e:`editorname` следующую строку.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Заметки  
 При вводе пути функция автозавершения пытается определить правильный путь и имя файла.  
  
## Пример  
 В приведенном примере в редакторе исходного кода открывается файл стилей Test1.css.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Окно интерпретации](../../ide/reference/immediate-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)