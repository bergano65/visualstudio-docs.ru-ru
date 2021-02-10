---
title: Команда Watch
description: Узнайте о команде Watch и о том, как она позволяет создать и открыть указанный экземпляр окна "Контрольное значение".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7c0530cf91467ec6c9bb2e6937b38510059041b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836180"
---
# <a name="watch-command"></a>Команда Watch
Создает и открывает указанный экземпляр окна **Контрольное значение** . Окно **Контрольные значения** можно использовать для вычисления значений переменных, выражений и регистров, чтобы изменять эти значения и сохранять результаты.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Аргументы

`index`\
Обязательный. Номер экземпляра окна контрольных значений

## <a name="remarks"></a>Комментарии

Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.

## <a name="example"></a>Пример

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>См. также раздел

- [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)
- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md) (Установка контрольных значений для переменных с помощью окон "Контрольное значение" и "Быстрая проверка")
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
