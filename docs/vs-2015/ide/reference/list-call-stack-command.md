---
title: Команда List Call Stack | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657658"
---
# <a name="list-call-stack-command"></a>Команда List Call Stack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 `index` Необязательный. Задает текущий кадр стека и не отображает выходные данные.

## <a name="switches"></a>Коммутаторы
 Каждый переключатель можно вызвать с помощью его полной или краткой формы.

 /Count: `number` [или]/c: `number` необязательный. Максимальное количество отображаемых стеков вызова. По умолчанию это значение не ограничено.

 /Шовтипес: `yes`&#124;`no` [или]/t: `yes`&#124;`no` необязательный. Указывает, отображать или нет типы параметров. Значение по умолчанию — `yes`.

 /Шовнамес: `yes`&#124;`no` [или]/n: `yes`&#124;`no` необязательный. Указывает, отображать или нет имена параметров. Значение по умолчанию — `yes`.

 /Шоввалуес: `yes`&#124;`no` [или]/v: `yes`&#124;`no` необязательный. Указывает, отображать или нет значения параметров. Значение по умолчанию: `yes`.

 /Шовмодуле: `yes`&#124;`no` [или]/m: `yes`&#124;`no` необязательный. Указывает, отображать или нет имя модуля. Значение по умолчанию — `yes`.

 /Шовлинеоффсет: `yes`&#124;`no` [или]/#: `yes`&#124;`no` необязательный. Указывает, отображать или нет смещение строки. Значение по умолчанию — `no`.

 /Шовбитеоффсет: `yes`&#124;`no` [или]/b: `yes`&#124;`no` необязательный. Указывает, отображать или нет байтовое смещение. Значение по умолчанию — `no`.

 /Шовлангуаже: `yes`&#124;`no` [или]/l: `yes`&#124;`no` необязательный. Указывает, отображать или нет используемый язык. Значение по умолчанию: `no`.

 /Инклудекаллсакросссреадс: `yes`&#124;`no` [или]/i: `yes`&#124;`no` необязательный. Указывает, включать или нет вызовы в другие потоки или из других потоков. Значение по умолчанию — `no`.

 /Шовекстерналкоде: `yes`&#124;`no` необязательный. Указывает, отображать или нет режим "Только мой код" для стека вызова. Если режим "Только мой код" выключен, отображается весь код, написанный не этим пользователем. Если режим "Только мой код" включен, то код, написанный не этим пользователем, отображается в выходных данных стека вызова как `[external]`.

 Thread: `n` необязательный. Отображает стек вызова для потока `n`. Если поток не указан, отображается стек вызова для текущего потока.

## <a name="remarks"></a>Remarks
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

## <a name="see-also"></a>См. также:
 [Список команд для дизассемблированного кода Дизассемблированный код](../../ide/reference/list-disassembly-command.md) [команда](../../ide/reference/list-threads-command.md) команд [Visual Studio Командная](../../ide/reference/visual-studio-commands.md) команда команда ["найти/команда"](../../ide/find-command-box.md) в командной [строке](../../ide/reference/command-window.md) [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
