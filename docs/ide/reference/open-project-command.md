---
title: "Команда Open Project | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject - команда"
  - "op - команда"
  - "Открыть проект - команда"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Команда Open Project
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открытие существующего проекта.  
  
## Синтаксис  
  
```  
File.OpenProject filename  
```  
  
## Аргументы  
 `filename`  
 Обязательный.  Полный путь и имя файла открываемого проекта.  
  
 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.  
  
## Заметки  
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода пользователем.  
  
 Эта команда недоступна во время отладки.  
  
## Пример  
 В этом примере открывается проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] — Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)