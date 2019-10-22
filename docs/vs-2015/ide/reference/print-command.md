---
title: Команда "Печать" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662160"
---
# <a name="print-command"></a>Команда Print
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вычисляет выражение или отображает указанный текст.

## <a name="syntax"></a>Синтаксис

```
Debug.Print text
```

## <a name="arguments"></a>Аргументы
 `text` Обязательный. Вычисляемое выражение или отображаемый текст.

## <a name="remarks"></a>Примечания
 Вы можете использовать вопросительный знак (?) в качестве псевдонима для этой команды. Таким образом, команда

```
>Debug.Print expA
```

 может быть записана в виде

```
>? expA
```

 Обе версии этой команды возвращают текущее значение выражения `expA`.

## <a name="example"></a>Пример

```
>Debug.Print varA
```

## <a name="see-also"></a>См. также
 [Команда "вычислить инструкцию](../../ide/reference/evaluate-statement-command.md) " команды [Visual Studio команды команд](../../ide/reference/visual-studio-commands.md) [](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
