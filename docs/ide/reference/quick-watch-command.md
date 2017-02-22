---
title: "Команда Quick Watch | Microsoft Docs"
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
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.QuickWatch - команда"
  - "Контрольное значение - команда"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Quick Watch
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображение выбранного или указанного текста в поле "Выражение" [диалогового окна "Быстрая проверка"](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md).  Можно использовать это диалоговое окно для расчета текущего значения переменной или выражения, распознаваемого отладчиком, или содержимого регистра.  Кроме того, можно изменить значение любой неконстантной переменной или содержимое любого регистра.  
  
## Синтаксис  
  
```  
Debug.QuickWatchq [text]  
```  
  
## Аргументы  
 `text`  
 Необязательный.  Текст, добавляемый в диалоговое окно **Быстрая проверка**.  
  
## Заметки  
 Если аргумент `text` не указан, в окно "Контрольное значение" добавляется выделенный в текущий момент текст или слово, на котором установлен курсор.  
  
## Пример  
  
```  
>Debug.QuickWatch  
```  
  
## См. также  
 [Практическое руководство. Использование диалогового окна быстрого просмотра](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)