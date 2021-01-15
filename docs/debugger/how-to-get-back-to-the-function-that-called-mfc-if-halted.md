---
title: Возврат к функции, вызвавшей MFC, при прерывании работы в MFC | Документация Майкрософт
description: Сведения о том, как вернуться к функции, вызвавшей MFC, если выполнение было прервано в отладчике Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 751688b72a7603e76733906775c594cd28e78c28
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148953"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Практическое руководство. Возврат к функции, вызвавшей MFC, при прерывании работы в MFC

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

При использовании команды **Прервать** из меню **Отладка** для остановки выполнения программы и завершения в MFC и при наличии ошибок в коде, можно вызвать окно "Стек вызовов" для обратного перехода к функции. Дополнительные сведения см. в разделе [Практическое руководство. использовать окно "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md).

Иногда код может прерываться в генераторе сообщений. В таком случае в стеке вызовов нет пользовательского кода. Во избежание этой проблемы используются точки останова (с условиями и количеством обращений) вместо команды **Прервать**. Для получения дополнительной информации см. [Breakpoints and Tracepoints](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Переход к функции, из которой был вызван MFC

- Используйте окно **Стек вызовов**.

## <a name="see-also"></a>См. также

- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)