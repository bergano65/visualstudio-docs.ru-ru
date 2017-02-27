---
title: "Команда List Memory | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory - команда"
  - "Вывести память - команда"
  - "ListMemory - команда"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Команда List Memory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображение содержимого указанного диапазона памяти.  
  
## Синтаксис  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## Аргументы  
 `expression`  
 Необязательный.  Адрес памяти, с которого начинается отображение памяти.  
  
## Переключатели  
 \/ANSI&#124;Unicode  
 Необязательный.  Отображает память в виде знаков ANSI или Unicode, соответствующих байтам памяти.  
  
 \/Count:`number`  
 Необязательный.  Определяет количество отображаемых байтов памяти, начиная с `expression`.  
  
 \/Format:`formattype`  
 Необязательный.  Тип формата для просмотра данных памяти в окне **Память**; может принимать следующие значения: OneByte, TwoBytes, FourBytes, EightBytes, Float \(32\-разрядный\) или Double \(64\-разрядный\).  При использовании значения OneByte параметр `/Unicode` недоступен.  
  
 \/Hex&#124;Signed&#124;Unsigned  
 Необязательный.  Устанавливает формат для просмотра чисел: signed \(со знаком\), unsigned \(без знака\) или hexadecimal \(шестнадцатеричные\).  
  
## Заметки  
 Вместо того, чтобы писать команду **Debug.ListMemory** полностью и со всеми переключателями, можно вызвать ее, используя стандартные псевдонимы с заданными значениями нужных переключателей.  Например, вместо ввода команды  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 можно написать следующее:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Ниже приведен список имеющихся псевдонимов для команды **Debug.ListMemory**:  
  
|Alias|Команда и переключатели|  
|-----------|-----------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory\/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## Пример  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## См. также  
 [Команда List Call Stack](../../ide/reference/list-call-stack-command.md)   
 [Команда List Threads](../../ide/reference/list-threads-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)