---
title: "Команда Set Current Thread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setcurrentthread"
helpviewer_keywords: 
  - "Debug.SetCurrentThread - команда"
  - "Задать текущий поток - команда"
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Команда Set Current Thread
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задает указанный поток в качестве текущего.  
  
## Синтаксис  
  
```  
Debug.SetCurrentThread index  
```  
  
## Аргументы  
 `index`  
 Обязательный.  Выбирает поток по индексу.  
  
## Пример  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)