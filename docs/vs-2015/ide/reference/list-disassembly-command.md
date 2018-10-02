---
title: Команда "Вывести дизассемблированный код" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6834bc8f6c9bc3aacb95ae3705195fde32c4d6cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569355"
---
# <a name="list-disassembly-command"></a>Команда List Disassembly
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда List Disassembly](https://docs.microsoft.com/visualstudio/ide/reference/list-disassembly-command).  
  
  
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
 Необязательный. Адрес, на котором нужно остановить дизассемблирование.  
  
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



