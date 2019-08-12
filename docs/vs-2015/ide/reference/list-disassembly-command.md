---
title: Команда "Вывести дизассемблированный код" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d361e5231d72df81fae164818bbe8341442c9f89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199174"
---
# <a name="list-disassembly-command"></a>Команда List Disassembly
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 Необязательный параметр. Количество инструкций для отображения. Значение по умолчанию — 8.  
  
 /endaddress: `expression` [или] /e: `expression`  
 Необязательный параметр. Адрес, на котором нужно остановить дизассемблирование.  
  
 /codebytes:`yes`&#124;`no` [или] /bytes:`yes`&#124;`no` [или] /b:`yes`&#124;`no`  
 Необязательный параметр. Указывает, следует ли отображать байты кода. Значение по умолчанию — `no`.  
  
 /source:`yes`&#124;`no` [или] /s:`yes`&#124;`no`  
 Необязательный параметр. Указывает, следует ли отображать исходный код. Значение по умолчанию — `no`.  
  
 /symbolnames:`yes`&#124;`no` [или] /names:`yes`&#124;`no` [или] /n:`yes`&#124;`no`  
 Необязательный параметр. Указывает, следует ли отображать имена символов. Значение по умолчанию — `yes`.  
  
 [/linenumbers:`yes`&#124;`no`]  
 Необязательный параметр. Включает просмотр номеров строк, связанных с исходным кодом. Параметр/source должен иметь значение `yes`, чтобы можно было использовать параметр /linenumbers.  
  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
