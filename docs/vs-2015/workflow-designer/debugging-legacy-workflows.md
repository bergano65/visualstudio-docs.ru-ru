---
title: Отладка устаревших рабочих процессов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656866"
---
# <a name="debugging-legacy-workflows"></a>Отладка рабочих процессов прежних версий
При использовании средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий в среде [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] для сборки приложений [!INCLUDE[wf](../includes/wf-md.md)], предназначенных для платформы .NET Framework 3.0 или 3.5, можно выполнять отладку рабочих процессов так же, как других программ, путем установки точек останова, присоединения к процессам, оценки потоков и стека вызова. Кроме того, существует возможность удаленной отладки.

> [!NOTE]
> Если на компьютере было установлено и удалено несколько версий Visual Studio, отладка WF3 может завершиться ошибкой по одной из следующих причин.
>
> - Не достигаются точки останова.
>   - Отображается следующее сообщение:
>
>   **Не удалось запустить отладку на веб-сервере. Отладчик установлен неправильно.  Не удается выполнить отладку запрошенного типа кода.  Запустите программу установки, чтобы установить или восстановить отладчик.**
>
>   Если один из этих сценариев возникает при отладке рабочего процесса .NET Framework 3.0 или 3.5, выполните исправление установки Visual Studio.

 [!INCLUDE[wf2](../includes/wf2-md.md)] интегрируется со следующими стандартными окнами отладки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:

- **Точка останова**: работает должным образом, но вы указываете действие для имени функции.

- **Стек вызовов**: изменен для предоставления структуры действий, выполненных в экземпляре рабочего процесса. Записи в окне **Стек вызовов** являются поиском по глубине в начале выполнения действий. Можно дважды щелкнуть по записи, чтобы поместить фокус на выбранное действие.

- **Потоки**: предоставляет идентификатор экземпляра для отлаживаемого экземпляра рабочего процесса.

  Visual Studio для Windows Workflow Foundation не поддерживает следующие возможности отладки:

- Условные точки останова на рабочей области конструктора операций.

- "Быстрая проверка".

- Задать следующий оператор.

- Выполнять до текущей позиции.

- Изменить и продолжить.

- JIT-отладка.

- Отладка в смешанном режиме.

## <a name="in-this-section"></a>Содержание
 [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Как отлаживать рабочие процессы, основанные на ASP.NET (для прежних версий)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Как задать точки останова в рабочих процессах (для прежних версий)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Отладка рабочих процессов с удаленного компьютера (для прежних версий)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Варианты пошаговой отладки (для прежних версий)](../workflow-designer/debug-stepping-options-legacy.md)

 [Как изменить вариант пошаговой отладки (для прежних версий)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)