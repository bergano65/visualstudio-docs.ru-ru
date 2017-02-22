---
title: "Команда Go To | Microsoft Docs"
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
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.GoTo - команда"
  - "Перейти - команда"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Go To
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перемещение курсора на указанную строку.  
  
## Синтаксис  
  
```  
Edit.GoTo [linenumber]  
```  
  
## Аргументы  
 `linenumber`  
 Необязательный.  Целое число, задающее номер строки, на которую необходимо перейти.  
  
## Заметки  
 Нумерация строк начинается с единицы.  Если значение `linenumber` меньше единицы, то отображается первая строка.  Если значение `linenumber` больше номера последней строки, то отображается последняя строка.  
  
 Если значение `linenumber` не указано, то отображается диалоговое окно **Переход на строку**.  
  
 Псевдоним для данной команды — GoToLn.  
  
## Пример  
  
```  
>Edit.GoTo 125  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)