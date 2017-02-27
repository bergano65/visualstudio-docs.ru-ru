---
title: "Команда List Disassembly | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly - команда"
  - "Вывести дизассемблированный код - команда"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Команда List Disassembly
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Запуск процесса отладки и определение порядка обработки ошибок.  
  
## Синтаксис  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## Переключатели  
 Каждый переключатель можно вызвать при помощи полной или краткой формы.  
  
 \/count: `number` \[или\] \/c: `number` \[или\] \/length: `number` \[или\] \/l: `number`  
 Необязательный.  Количество отображаемых инструкций.  По умолчанию установлено значение 8.  
  
 \/endaddress: `expression` \[или\] \/e: `expression`  
 Необязательный.  Адрес, в котором останавливается дизассемблирование.  
  
 \/codebytes:`yes`&#124;`no` \[или\] \/bytes:`yes`&#124;`no` \[или\] \/b:`yes`&#124;`no`  
 Необязательный.  Указывает, отображать или нет байты программного кода.  Значение по умолчанию — `no`.  
  
 \/source:`yes`&#124;`no` \[или\] \/s:`yes`&#124;`no`  
 Необязательный.  Указывает, отображать или нет исходный код.  Значение по умолчанию — `no`.  
  
 \/symbolnames:`yes`&#124;`no` \[или\] \/names:`yes`&#124;`no` \[или\] \/n:`yes`&#124;`no`  
 Необязательный.  Указывает, отображать или нет имена символов.  Значение по умолчанию — `yes`.  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 Необязательный.  Включает просмотр номеров строк, ассоциированных с исходным кодом.  Переключатель \/source должен иметь значение `yes`, чтобы можно было использовать переключатель \/linenumbers.  
  
## Пример  
  
```  
>Debug.ListDisassembly  
```  
  
## См. также  
 [Команда List Call Stack](../../ide/reference/list-call-stack-command.md)   
 [Команда List Threads](../../ide/reference/list-threads-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)