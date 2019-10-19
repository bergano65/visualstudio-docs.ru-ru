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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672743"
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

 /Count: `number` [или]/c: `number` [или]/ленгс: `number` [или]/l: `number` необязательный. Количество инструкций для отображения. Значение по умолчанию — 8.

 /ендаддресс: `expression` [или]/e: `expression` необязательный. Адрес, на котором нужно остановить дизассемблирование.

 /кодебитес: `yes`&#124; `no` [или]/bytes: `yes`&#124; `no` [или]/b: `yes`&#124; `no` необязательный. Указывает, следует ли отображать байты кода. Значение по умолчанию — `no`.

 /Source: `yes`&#124; `no` [или]/s: `yes`&#124; `no` необязательный. Указывает, следует ли отображать исходный код. Значение по умолчанию — `no`.

 /симболнамес: `yes`&#124; `no` [или]/names: `yes`&#124; `no` [или]/n: `yes`&#124; `no` необязательно. Указывает, следует ли отображать имена символов. Значение по умолчанию — `yes`.

 [/линенумберс: `yes`&#124; `no`] Используемых. Включает просмотр номеров строк, связанных с исходным кодом. Параметр/source должен иметь значение `yes`, чтобы можно было использовать параметр /linenumbers.

## <a name="example"></a>Пример

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>См. также
 Список [команд стека вызовов](../../ide/reference/list-call-stack-command.md) [Командная команда](../../ide/reference/list-threads-command.md) [Visual Studio](../../ide/reference/visual-studio-commands.md) [команды команд](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
