---
title: "Команда Start | Microsoft Docs"
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
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start - команда"
  - "Запуск - команда"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Start
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Начинает отладку запускаемого проекта.  
  
## Синтаксис  
  
```  
Debug.Start [address]  
```  
  
## Аргументы  
 `address`  
 Необязательный.  Адрес, в котором останавливается выполнение программы, сходен с точкой останова в исходном коде.  Этот аргумент допускается только в режиме отладки.  
  
## Заметки  
 При исполнении команды **Start** выполняется операция RunToCursor по указанному адресу.  
  
## Пример  
 В данном примере запускается отладчик и пропускаются все исключения, которые происходят.  
  
```  
>Debug.Start  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)