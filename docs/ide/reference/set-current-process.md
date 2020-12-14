---
title: Команда Set Current Process
description: Сведения о команде Set Current Process и о том, как с ее помощью задать указанный процесс в качестве активного процесса в отладчике.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b6a5c2f010b60546fe1ece16f66bf437d2dc633
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616588"
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

## <a name="remarks"></a>Remarks
Во время отладки можно подключиться к нескольким процессам, но в любой момент времени только один из них будет активным в отладчике. Чтобы задать активный процесс, можно использовать команду `SetCurrentProcess`.

## <a name="example"></a>Пример

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
