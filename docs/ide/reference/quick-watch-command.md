---
title: Команда Quick Watch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75afe1cdd0d1755d2953e6b9e6e3e85a089b3303
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926126"
---
# <a name="quick-watch-command"></a>Команда Quick Watch
Отображает выбранный или указанный текст в поле "Выражение" окна [Быстрая проверка](../../debugger/watch-and-quickwatch-windows.md). Это диалоговое окно предназначено для вычисления текущего значения переменной или выражения, распознанного отладчиком, либо содержимого регистра. Кроме того, можно изменить значение любой неконстантной переменной или содержимое регистров.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Аргументы

`text`\
Необязательный параметр. Текст для добавления в диалоговое окно **Быстрая проверка**

## <a name="remarks"></a>Примечания

Если параметр `text` опущен, выделенный текст или слово в позиции курсора добавляется в окно контрольных значений.

## <a name="example"></a>Пример

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>См. также

- [Установка контрольных значений для переменных с помощью окон "Контрольное значение" и "Быстрая проверка" в Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)