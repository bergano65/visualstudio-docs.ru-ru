---
title: Команда Set Current Process
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c01c399dc76d1b328443edef27edd9a921b1b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855287"
---
# <a name="set-current-process"></a>Команда Set Current Process
Задает указанный процесс в качестве активного процесса в отладчике.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Аргументы
 `index`

 Обязательный. Индекс процесса.

## <a name="remarks"></a>Примечания
 Во время отладки можно подключиться к нескольким процессам, но в любой момент времени только один из них будет активным в отладчике. Чтобы задать активный процесс, можно использовать команду `SetCurrentProcess`.

## <a name="example"></a>Пример

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)