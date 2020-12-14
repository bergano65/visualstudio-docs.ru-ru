---
title: Команда Set Current Thread
description: Сведения о команде Set Current Thread и о том, как с ее помощью задать указанный поток в качестве текущего.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cedd37ece7bcc0eb79ad52cc426b07f8cb2ca57
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616568"
---
# <a name="set-current-thread-command"></a>Команда Set Current Thread
Задает указанный поток в качестве текущего.

## <a name="syntax"></a>Синтаксис

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Аргументы
`index`

Обязательный. Выбирает поток по индексу.

## <a name="example"></a>Пример

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)