---
title: "Команда List Registers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters - команда"
  - "Вывести регистры - команда"
  - "ListRegisters - команда"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Команда List Registers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображает значения выбранных регистров и позволяет вносить изменения в список отображаемых регистров.  
  
## Синтаксис  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## Переключатели  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 Отображает значения заданных элементов `register` или `registerGroup`.  Если элементы `register` или `registerGroup` не заданы, отображается список регистров по умолчанию.  Если этот переключатель не указан, поведение будет таким же.  Примеры.  
  
 `Debug.ListRegisters /Display eax`  
  
 , эквивалентно выражению  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 Отображает все группы регистров в списке.  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 Добавляет к списку одно или несколько значений `register` или `registerGroup`.  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 Удаляет из списка одно или несколько значений `register` или `registerGroup`.  
  
## Заметки  
 Вместо `Debug.ListRegisters` можно использовать псевдоним `r`.  
  
## Пример  
 В данном примере для отображения значений группы регистров `Flags` вместо `Debug.ListRegisters` используется псевдоним `r`.  
  
```  
r /Display Flags  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Общие сведения об отладке: окно регистров](../../debugger/debugging-basics-registers-window.md)   
 [Практическое руководство. Использование окна регистров](../../debugger/how-to-use-the-registers-window.md)