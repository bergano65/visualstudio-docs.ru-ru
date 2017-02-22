---
title: "Команда Add Existing Item | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addexistingitem"
helpviewer_keywords: 
  - "Добавить существующий элемент - команда"
  - "File.AddExistingItem - команда"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Add Existing Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Добавление существующего файла в текущее решение и открытие этого файла.  
  
## Синтаксис  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## Аргументы  
 `filename`  
 Обязательный.  Полный путь и имя файла с расширением элемента, который необходимо добавить в текущее решение.  Если путь к файлу или имя файла содержит пробелы, то полный путь к файлу необходимо заключить в кавычки.  
  
## Переключатели  
 \/e: `editorname`  
 Необязательный.  Имя редактора, в котором будет открыт файл.  Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента \/e:`editorname` имена редакторов используются в том виде, в каком они отображаются в **диалоговом окне "Открыть с помощью"**, с заключением в кавычки.  Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента \/e:`editorname` следующую строку.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Заметки  
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода пользователем.  
  
## Пример  
 В этом примере в текущее решение добавляется файл Form1.frm.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)