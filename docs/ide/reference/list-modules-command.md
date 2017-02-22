---
title: "Команда List Modules | Microsoft Docs"
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
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules - команда"
  - "Вывести модули - команда"
  - "ListModules - команда"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда List Modules
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображение списка модулей для текущего процесса.  
  
## Синтаксис  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### Параметры  
 \/Address:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать адреса памяти модулей.  Значение по умолчанию — `yes`.  
  
 \/Name:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать имена модулей.  Значение по умолчанию — `yes`.  
  
 \/Order:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать порядок модулей.  Значение по умолчанию — `no`.  
  
 \/Path:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать пути модулей.  Значение по умолчанию — `yes`.  
  
 \/Process:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать процессы модулей.  Значение по умолчанию — `no`.  
  
 \/SymbolFile:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать файлы символов модулей.  Значение по умолчанию — `no`.  
  
 \/SymbolStatus:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать состояния символов модулей.  Значение по умолчанию — `yes`.  
  
 \/Timestamp:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать метки времени модулей.  Значение по умолчанию — `no`.  
  
 \/Version:`yes|no`  
 Необязательный.  Указывает, нужно ли отображать версии модулей.  Значение по умолчанию — `no`.  
  
## Заметки  
  
## Пример  
 Этот пример иллюстрирует создание списка имен модулей для текущего процесса с указанием адресов и меток времени.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Практическое руководство. Использование окна модулей](../../debugger/how-to-use-the-modules-window.md)