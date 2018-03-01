---
title: "Команда \"Вывести дизассемблированный код\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c6a704ac783f4efc300de26c2a5e987f82fc2e9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="list-disassembly-command"></a>Команда List Disassembly
Начинает процесс отладки и позволяет указать способ обработки ошибок.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Переключатели  
 Каждый переключатель можно вызвать с помощью его полной или краткой формы.  
  
 /count: `number` [или] /c: `number` [или] /length: `number` [или] /l: `number`  
 Необязательный. Количество инструкций для отображения. Значение по умолчанию — 8.  
  
 /endaddress: `expression` [или] /e: `expression`  
 Необязательно. Адрес, на котором нужно остановить дизассемблирование.  
  
 /codebytes:`yes`&#124;`no` [или] /bytes:`yes`&#124;`no` [или] /b:`yes`&#124;`no`  
 Необязательный. Указывает, следует ли отображать байты кода. Значение по умолчанию — `no`.  
  
 /source:`yes`&#124;`no` [или] /s:`yes`&#124;`no`  
 Необязательный. Указывает, следует ли отображать исходный код. Значение по умолчанию — `no`.  
  
 /symbolnames:`yes`&#124;`no` [или] /names:`yes`&#124;`no` [или] /n:`yes`&#124;`no`  
 Необязательный. Указывает, следует ли отображать имена символов. Значение по умолчанию — `yes`.  
  
 [/linenumbers:`yes`&#124;`no`]  
 Необязательный. Включает просмотр номеров строк, связанных с исходным кодом. Параметр/source должен иметь значение `yes`, чтобы можно было использовать параметр /linenumbers.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>См. также  
 [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)   
 [Команда List Thread](../../ide/reference/list-threads-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)