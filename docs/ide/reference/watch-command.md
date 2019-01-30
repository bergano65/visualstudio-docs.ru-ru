---
title: Команда Watch
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f979162dbbef7c04372d42d9ab693b013f33b8ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923339"
---
# <a name="watch-command"></a>Команда Watch
Создает и открывает указанный экземпляр окна **Контрольное значение** . Окно **Контрольные значения** можно использовать для вычисления значений переменных, выражений и регистров, чтобы изменять эти значения и сохранять результаты.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Аргументы
 `index`

 Обязательный. Номер экземпляра окна контрольных значений

## <a name="remarks"></a>Примечания
 Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.

## <a name="example"></a>Пример

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>См. также раздел

- [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)
- [Установка контрольных значений для переменных с помощью окон "Контрольное значение" и "Быстрая проверка" в Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)