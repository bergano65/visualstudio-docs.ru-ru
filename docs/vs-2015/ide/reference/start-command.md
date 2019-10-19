---
title: Команда "Запустить" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663496"
---
# <a name="start-command"></a>Команда Start
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Начинает отладку запускаемого проекта.

## <a name="syntax"></a>Синтаксис

```
Debug.Start [address]
```

## <a name="arguments"></a>Аргументы
 `address` Необязательный. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.

## <a name="remarks"></a>Примечания
 При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.

## <a name="example"></a>Пример
 Этот пример запускает отладчик и игнорирует все возникающие исключения.

```
>Debug.Start
```

## <a name="see-also"></a>См. также
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
