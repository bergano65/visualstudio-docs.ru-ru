---
title: "Команда List Call Stack | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 409c9434f54688b2088552397377957a1f8985d3
ms.lasthandoff: 02/22/2017

---
# <a name="list-call-stack-command"></a>Команда List Call Stack
Отображает текущий стек вызовов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Необязательно. Задает текущий кадр стека и не отображает выходные данные.  
  
## <a name="switches"></a>Переключатели  
 Каждый переключатель можно вызвать с помощью его полной или краткой формы.  
  
 /Count:`number` [или] /C:`number`  
 Необязательно. Максимальное количество отображаемых стеков вызова. По умолчанию это значение не ограничено.  
  
 /ShowTypes:`yes`|`no` [или] /T:`yes`|`no`  
 Необязательно. Указывает, отображать или нет типы параметров. Значение по умолчанию — `yes`.  
  
 /ShowNames:`yes`|`no` [или] /N:`yes`|`no`  
 Необязательно. Указывает, отображать или нет имена параметров. Значение по умолчанию — `yes`.  
  
 /ShowValues:`yes`|`no` [или] /V:`yes`|`no`  
 Необязательно. Указывает, отображать или нет значения параметров. Значение по умолчанию — `yes`.  
  
 /ShowModule:`yes`|`no` [или] /M:`yes`|`no`  
 Необязательно. Указывает, отображать или нет имя модуля. Значение по умолчанию — `yes`.  
  
 /ShowLineOffset:`yes`|`no` [или] /#:`yes`|`no`  
 Необязательно. Указывает, отображать или нет смещение строки. Значение по умолчанию — `no`.  
  
 /ShowByteOffset:`yes`|`no` [или] /B:`yes`|`no`  
 Необязательно. Указывает, отображать или нет байтовое смещение. Значение по умолчанию — `no`.  
  
 /ShowLanguage:`yes`|`no` [или] /L:`yes`|`no`  
 Необязательно. Указывает, отображать или нет используемый язык. Значение по умолчанию — `no`.  
  
 /IncludeCallsAcrossThreads:`yes`|`no` [или] /I:`yes`|`no`  
 Необязательно. Указывает, включать или нет вызовы в другие потоки или из других потоков. Значение по умолчанию — `no`.  
  
 /ShowExternalCode:`yes`|`no`  
 Необязательно. Указывает, отображать или нет режим "Только мой код" для стека вызова. Если режим "Только мой код" выключен, отображается весь код, написанный не этим пользователем. Если режим "Только мой код" включен, то код, написанный не этим пользователем, отображается в выходных данных стека вызова как `[external]`.  
  
 Thread:`n`  
 Необязательно. Отображает стек вызова для потока `n`. Если поток не указан, отображается стек вызова для текущего потока.  
  
## <a name="remarks"></a>Примечания  
 Изменения аргументов или переключателей применяются при последующих вызовах данной команды. При выполнении самой команды Debug.ListCallStackby отображается весь стек вызова. При указании индекса, например,  
  
```  
Debug.ListCallStack 2  
```  
  
 текущий кадр стека устанавливается на этот кадр (в данном случае на второй).  
  
 Для вызова этой команды можно также использовать ее стандартный псевдоним "kb". Например, можно ввести  
  
```  
kb 2  
```  
  
 для установки текущего кадра стека на второй кадр.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>См. также  
 [Команда List Disassembly](../../ide/reference/list-disassembly-command.md)   
 [Команда List Thread](../../ide/reference/list-threads-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
