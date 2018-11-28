---
title: 'Практическое: вернуться к функции, вызвавшей MFC, при прерывании работы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af8856a4356a829b37a4a624b86f7b29dd965f9c
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389462"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Практическое руководство. Возврат к функции, вызвавшей MFC, при прерывании работы в MFC

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

При использовании команды Прервать **из меню Отладка** для остановки выполнения программы и завершения в MFC и при наличии ошибок в коде, можно вызвать окно "Стек вызовов" для обратного перехода к функции. Дополнительные сведения см. в разделе [как: использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md).

Иногда код может прерываться в генераторе сообщений. В таком случае в стеке вызовов нет пользовательского кода. Во избежание этой проблемы используются точки останова (с условиями и числами попаданий) вместо команды Прервать **. Для получения дополнительной информации см. [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Перейдите к функции, из которого был вызван MFC

-   Используйте окно Стек вызовов **.

## <a name="see-also"></a>См. также

- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)