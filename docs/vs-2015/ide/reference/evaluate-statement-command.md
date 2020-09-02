---
title: Команда "Вычислить оператор" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657711"
---
# <a name="evaluate-statement-command"></a>Команда Evaluate Statement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вычисляет и отображает заданный оператор.

## <a name="syntax"></a>Синтаксис

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Аргументы
 `text` Обязательный. Вычисляемый оператор.

## <a name="remarks"></a>Remarks
 Окно, используемое для ввода команды **EvaluateStatement**, определяет, интерпретируется ли знак равенства (=) как оператор сравнения или оператор присваивания.

 В **командном окне** знак равенства (=) интерпретируется как оператор сравнения. Например, если значения переменных `a` и `b` различаются, то команда

```
>Debug.EvaluateStatement(a=b)
```

 возвращает значение `false`.

 В окне **интерпретации**, напротив, знак равенства (=) интерпретируется как оператор присваивания. Таким образом, команда

```
>Debug.EvaluateStatement(a=b)
```

 присвоит переменной `a` значение переменной `b`.

## <a name="example"></a>Пример

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>См. также:
 [Команда Print](../../ide/reference/print-command.md) Командная кнопка [Visual Studio Командная](../../ide/reference/visual-studio-commands.md) [команда](../../ide/reference/command-window.md) [Поиск/команда](../../ide/find-command-box.md) Командная кнопка [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
