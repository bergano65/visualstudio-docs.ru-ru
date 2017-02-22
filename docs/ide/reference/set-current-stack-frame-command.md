---
title: "Команда Set Current Stack Frame | Microsoft Docs"
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
  - "debug.setcurrentstackframe"
helpviewer_keywords: 
  - "Debug.SetCurrentStackFrame - команда"
  - "Задать текущий кадр стека - команда"
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Set Current Stack Frame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Эта команда позволяет указать определенный кадр стека.  
  
## Синтаксис  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## Аргументы  
 `index`  
 Обязательный.  Выбирает кадр стека по его индексу.  
  
## Пример  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)