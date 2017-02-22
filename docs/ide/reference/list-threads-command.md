---
title: "Команда List Threads | Microsoft Docs"
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
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads - команда"
  - "Вывести потоки - команда"
  - "ListThreads - команда"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда List Threads
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображение списка потоков в текущей программе.  
  
## Синтаксис  
  
```  
Debug.ListThreads [index]  
```  
  
## Аргументы  
 `index`  
 Необязательный.  Назначает выбранный по индексу поток в качестве текущего.  
  
## Заметки  
 Если этот аргумент указан, то аргумент `index` отмечает указанный поток в качестве текущего.  Рядом с текущим потоком в списке отображается символ звездочки \(\*\).  
  
## Пример  
  
```  
>Debug.ListThreads   
```  
  
## См. также  
 [Команда List Call Stack](../../ide/reference/list-call-stack-command.md)   
 [Команда List Disassembly](../../ide/reference/list-disassembly-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)