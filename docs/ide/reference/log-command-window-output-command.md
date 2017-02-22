---
title: "Команда Log Command Window Output | Microsoft Docs"
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
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "Запись вывода окна команд - команда"
  - "View.LogCommandWindowOutput - команда"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Log Command Window Output
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Выполнение копирования всех входных и выходных данных из окна **Команда**.  
  
## Синтаксис  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## Аргументы  
 `filename`  
 Необязательный.  Имя системного журнала.  По умолчанию файл создается в папке пользовательского профиля.  Если имя файла уже существует, записи добавляются в конец существующего файла.  Если файл не определен, используется последний из указанных ранее файлов.  Если предыдущего файла нет, создается файл журнала по умолчанию с именем cmdline.log.  
  
> [!TIP]
>  Чтобы изменить место хранения файла журнала, введите полный путь файла, заключив его в кавычки, если путь содержит пробелы.  
  
## Переключатели  
 \/on  
 Необязательный.  Запуск протоколирования для окна **Команда** с выводом в указанный файл; новые сведения добавляются в файл.  
  
 \/off  
 Необязательный.  Прекращение протоколирования для окна **Команда**.  
  
 \/overwrite  
 Необязательный.  Если файл, указанный в аргументе `filename`, совпадает с существующим файлом, файл перезаписывается.  
  
## Заметки  
 Если файл не определен, по умолчанию создается файл cmdline.log.  По умолчанию для данной команды используется псевдоним Log.  
  
## Примеры  
 В этом примере создается новый файл журнала cmdlog и в него начинает вестись запись данных по командам.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 В этом примере выполняется остановка ведения журнала по командам.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 В этом примере возобновляется ведение журнала по командам в ранее использовавшийся файл журнала.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)