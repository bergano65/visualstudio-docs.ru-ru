---
title: "Команда Toggle Breakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint - команда"
  - "Точка останова - команда"
  - "ToggleBreakpoint - команда"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Команда Toggle Breakpoint
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Включение или выключение точки останова в текущем расположении в файле в зависимости от ее текущего состояния.  
  
## Синтаксис  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## Аргументы  
 `text`  
 Необязательный.  Если указан аргумент text, строка маркируется как именованная точка останова.  В противном случае строка маркируется как безымянная точка остановка, что сходно с результатом нажатия клавиши F9.  
  
## Пример  
 В следующем примере выполняется переключение текущей точки останова.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)