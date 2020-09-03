---
title: Команда "Вывести память" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672748"
---
# <a name="list-memory-command"></a>Команда List Memory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает содержимое указанного диапазона памяти.

## <a name="syntax"></a>Синтаксис

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Аргументы
 `expression` Необязательный. Адрес памяти, с которого начинается отображение памяти.

## <a name="switches"></a>Коммутаторы
 /АНСИ&#124;Юникод необязательно. Отображает память в виде символов, соответствующих байтам памяти, в формате ANSI или Юникод.

 /Count: `number` необязательный. Определяет, сколько байт памяти нужно отобразить, начиная с `expression`.

 /Format: `formattype` необязательный. Тип формата для просмотра данных памяти в окне **Память**, может иметь значение OneByte, TwoBytes, FourBytes, EightBytes, Float (32-разрядный) или Double (64-разрядный). При использовании OneByte параметр `/Unicode` недоступен.

 /Хекс&#124;со знаком&#124;без подписи необязательно. Указывает формат для просмотра чисел: со знаком, без знака или в шестнадцатеричном формате.

## <a name="remarks"></a>Remarks
 Вместо записи полной команды **Debug.ListMemory** со всеми параметрами можно вызвать ее, используя стандартные псевдонимы, в которых отдельные параметры уже имеют определенные значения. Например, вместо ввода:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 можно ввести:

```
>df /Count:30 /Unicode
```

 Ниже приведен список доступных псевдонимов для команды **Debug.ListMemory**:

|Псевдоним|Команда и параметры|
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**базе**|Debug.ListMemory /Format:OneByte|
|**Постоянный**|Debug.ListMemory /Format:FourBytes /Ansi|
|**DDL**|Debug.ListMemory /Format:FourBytes|
|**DF**|Debug.ListMemory /Format:Float|
|**DQ**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Пример

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>См. также:
 Список [команд стека вызовов](../../ide/reference/list-call-stack-command.md) [Командная команда](../../ide/reference/list-threads-command.md) [Visual Studio](../../ide/reference/visual-studio-commands.md) [команды команд](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
