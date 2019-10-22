---
title: Команда List Modules | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659529"
---
# <a name="list-modules-command"></a>Команда List Modules
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает список модулей для текущего процесса.

## <a name="syntax"></a>Синтаксис

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Параметры
 /Аддресс: `yes|no` необязательный. Указывает, нужно ли отображать адреса модулей в памяти. Значение по умолчанию — `yes`.

 /Name:`yes|no` (необязательно). Указывает, нужно ли отображать имена модулей. Значение по умолчанию — `yes`.

 /Order: `yes|no` необязательный. Указывает, нужно ли отображать порядок модулей. Значение по умолчанию — `no`.

 /Path:`yes|no` (необязательно). Указывает, нужно ли отображать пути к модулям. Значение по умолчанию — `yes`.

 /Process: `yes|no` необязательный. Указывает, нужно ли отображать процессы модулей. Значение по умолчанию — `no`.

 /Симболфиле: `yes|no` необязательный. Указывает, нужно ли отображать файлы символов модулей. Значение по умолчанию — `no`.

 /Симболстатус: `yes|no` необязательный. Указывает, нужно ли отображать состояния символов модулей. Значение по умолчанию — `yes`.

 /Тиместамп: `yes|no` необязательный. Указывает, нужно ли отображать метки времени модулей. Значение по умолчанию — `no`.

 /Version:`yes|no` (необязательно). Указывает, нужно ли отображать версии модулей. Значение по умолчанию — `no`.

## <a name="remarks"></a>Примечания

## <a name="example"></a>Пример
 В этом примере демонстрируется создание списка имен модулей для текущего процесса с указанием адресов и меток времени.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>См. также
 Команда [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [. как использовать окно "модули"](../../debugger/how-to-use-the-modules-window.md)
