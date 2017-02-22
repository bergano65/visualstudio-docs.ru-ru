---
title: "Команда Set Current Process | Microsoft Docs"
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
  - "Debug.SetCurrentProcess - команда"
  - "Задать текущий процесс - команда"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Set Current Process
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задание указанного процесса в качестве активного процесса в отладчике.  
  
## Синтаксис  
  
```  
Debug.SetCurrentProcess index  
```  
  
## Аргументы  
 `index`  
 Обязательный.  Индекс процесса.  
  
## Заметки  
 Во время отладки можно подключиться к нескольким процессам, но в любой момент времени только один из них будет активным в отладчике.  Чтобы задать активный процесс, можно использовать команду `SetCurrentProcess`.  
  
## Пример  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)