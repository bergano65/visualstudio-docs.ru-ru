---
title: Команда Set Current Process
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d8c313eebc8623156dd7a575060397ee6e16a9d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748640"
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

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)