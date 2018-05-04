---
title: Команда Watch
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97fe1c6865b8934d2c0329547e98323c75bf3ec0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="watch-command"></a>Команда Watch
Создает и открывает указанный экземпляр окна **Контрольное значение** . Окно **Контрольные значения** можно использовать для вычисления значений переменных, выражений и регистров, чтобы изменять эти значения и сохранять результаты.

## <a name="syntax"></a>Синтаксис

```
Debug.Watch[index]
```

## <a name="arguments"></a>Аргументы
 `index`

 Обязательно. Номер экземпляра окна контрольных значений

## <a name="remarks"></a>Примечания
 Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.

## <a name="example"></a>Пример

```
>Debug.Watch1
```

## <a name="see-also"></a>См. также

- [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)
- [Установка контрольных значений для переменных с помощью окон "Контрольное значение" и "Быстрая проверка" в Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)