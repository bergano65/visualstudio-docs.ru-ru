---
title: "Команда Watch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch - команда"
  - "Watch - команда"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Команда Watch
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Создание и открытие указанного экземпляра окна **Контрольные значения**.  Окно **Контрольные значения** можно использовать для расчета значений переменных, выражений и регистров, а также для изменения этих значений и сохранения результатов.  
  
## Синтаксис  
  
```  
Debug.Watch[index]  
```  
  
## Аргументы  
 `index`  
 Обязательный.  Номер экземпляра окна контрольных значений.  
  
## Заметки  
 Значением аргумента `index` должно быть целое число.  Допустимые значения: 1, 2, 3 или 4.  
  
## Пример  
  
```  
>Debug.Watch1  
```  
  
## См. также  
 [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)   
 [Практическое руководство. Изменение значения в окне переменной](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [Практическое руководство. Использование диалогового окна быстрого просмотра](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)