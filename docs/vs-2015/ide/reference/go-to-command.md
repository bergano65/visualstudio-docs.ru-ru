---
title: Команда "Перейти" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661205"
---
# <a name="go-to-command"></a>команда «Перейти к»
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Перемещение курсор на указанную строку.

## <a name="syntax"></a>Синтаксис

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Аргументы
 `linenumber` Необязательный. Целое число, задающее номер строки, к которой нужно перейти.

## <a name="remarks"></a>Remarks
 Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.

 Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.

 Эта команда имеет псевдоним GoToLn.

## <a name="example"></a>Пример

```
>Edit.GoTo 125
```

## <a name="see-also"></a>См. также:
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
