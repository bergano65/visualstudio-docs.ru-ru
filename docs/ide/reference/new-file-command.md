---
title: "Команда New File | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile - команда"
  - "Создать файл - команда"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда New File
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Создание и открытие нового файла.  Файл появляется в папке "Прочие файлы".  
  
## Синтаксис  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## Аргументы  
 `filename`  
 Необязательный.  Имя файла.  Если имя не определено, используется имя по умолчанию.  Если имя шаблона не указано, создается текстовый файл.  
  
## Переключатели  
 \/t:`templatename`  
 Необязательный.  Указывает тип создаваемого файла.  
  
 \/t: синтаксис аргумента`templatename` используются данные, находящиеся в диалоговом окне создание файла.  Введите имя категории, затем обратную косую черту \(`\`\) и имя шаблона. Заключите всю строку в кавычки.  
  
 Например, чтобы создать новый файл исходного кода [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)], для аргумента \/t:`templatename` необходимо ввести следующую строку.  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 В приведенном выше примере указано, что шаблон файла C\+\+ находится в диалоговом окне **Создание файла** под категорией Visual C\+\+.  
  
 \/e:`editorname`  
 Необязательный.  Имя редактора, в котором будет открыт файл.  Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 \/e: синтаксис аргумента`editorname` используются имена в редакторе по мере их появления в диалоговое окно открыть с помощью ", заключенные в кавычки.  
  
 Например, чтобы открыть файл в редакторе исходного кода, необходимо ввести для аргумента \/e:`editorname` следующую строку.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Пример  
 В приведенном примере создается новая веб\-страница "test1.htm", которая открывается в редакторе исходного кода.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Окно интерпретации](../../ide/reference/immediate-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)