---
title: Команда "Задать текущий процесс" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665468"
---
# <a name="set-current-process"></a>Команда Set Current Process
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает указанный процесс в качестве активного процесса в отладчике.

## <a name="syntax"></a>Синтаксис

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Аргументы
 `index` Обязательный. Индекс процесса.

## <a name="remarks"></a>Примечания
 Во время отладки можно подключиться к нескольким процессам, но в любой момент времени только один из них будет активным в отладчике. Чтобы задать активный процесс, можно использовать команду `SetCurrentProcess`.

## <a name="example"></a>Пример

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>См. также
 Команды [Visual Studio](../../ide/reference/visual-studio-commands.md) командное [окно](../../ide/reference/command-window.md) команд [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
