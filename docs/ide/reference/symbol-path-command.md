---
title: "Команда Symbol Path | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath - команда"
  - "Путь к символам - команда"
  - "SymbolPath - команда"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Команда Symbol Path
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Определение списка каталогов для поиска символов отладчиком.  
  
## Синтаксис  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## Аргументы  
 `pathname`  
 Необязательный параметр.  Список путей \(через точку с запятой\) для поиска символов отладчиком.  
  
## Заметки  
 Если `pathname` не указано, команда выводит список текущих путей к символам.  
  
## Пример  
 В этом примере в список каталогов символов добавляется два пути.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## Пример  
 В этом примере выводится список текущих путей к символам \(через точку с запятой\).  
  
```  
Debug.SymbolPath  
```  
  
## См. также  
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)