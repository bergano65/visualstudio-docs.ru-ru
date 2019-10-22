---
title: Команда Watch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604832"
---
# <a name="watch-command"></a>Команда Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создает и открывает указанный экземпляр окна **Контрольное значение** . Окно **Контрольные значения** можно использовать для вычисления значений переменных, выражений и регистров, чтобы изменять эти значения и сохранять результаты.

## <a name="syntax"></a>Синтаксис

```
Debug.Watch[index]
```

## <a name="arguments"></a>Аргументы
 `index` Обязательный. Номер экземпляра окна контрольных значений

## <a name="remarks"></a>Примечания
 Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.

## <a name="example"></a>Пример

```
>Debug.Watch1
```

## <a name="see-also"></a>См. также
 [Окна "видимые" и "Локальные](../../debugger/autos-and-locals-windows.md) " [. как изменить значение в окне переменных](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [. как использовать диалоговое окно "Быстрая проверка](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) " [команды Visual Studio](../../ide/reference/visual-studio-commands.md) команда ["найти/команда"](../../ide/find-command-box.md) в [окне](../../ide/reference/command-window.md) команд Visual Studio командные [псевдонимы](../../ide/reference/visual-studio-command-aliases.md)
