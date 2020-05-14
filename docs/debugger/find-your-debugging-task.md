---
title: Поиск задачи отладки
description: Определение функции отладчика, которая поможет отладить приложение
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301149"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Поиск задачи отладки в Visual Studio

Если вам нужна помощь по сопоставлению задачи отладки с соответствующей функцией отладчика Visual Studio, используйте ссылки из этой статьи. Приведенный здесь список задач содержит типичные задачи, такие как приостановка кода для отладки, проверка переменных и отправка сообщений в окно **вывода**. Если вам нужны общие сведения о функциях отладчика, обратитесь к разделу [Первое знакомство с отладчиком](debugger-feature-tour.md).

## <a name="pause-running-code"></a>Приостановка выполнения кода

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Приостановка выполнения кода для проверки строки кода, которая может содержать ошибку

Задайте точку останова. Для получения дополнительной информации см. раздел [Использование точек останова](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Приостановка и проверка приложения при достижении определенного состояния

Используйте условную точку останова, чтобы управлять тем, где и когда точка останова активируется, с помощью условной логики. Дополнительные сведения см. в разделе [Условия точек останова](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Приостановка кода только при изменении значения или свойства конкретного объекта

Для C++ задайте [точку останова в данных](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
Для приложений, использующих .NET Core 3, можно также задать [точку останова в данных](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

В противном случае, только для C# и F#, можно [отслеживать идентификатор объекта с помощью условной точки останова](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Приостановка кода внутри цикла на определенной итерации

Задайте точку останова, используя **количество обращений** в качестве условия. Дополнительные сведения см. в разделе [Количество обращений](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Приостановка кода в начале функции, когда известно имя функции, но не ее расположение

Это можно сделать с помощью точки останова в функции. Дополнительные сведения см. в разделе [Задание точек останова в функции](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Приостановка кода в начале нескольких функций с одинаковым именем

При наличии нескольких функций с одинаковыми именами (перегруженные функции или функции в разных проектах) можно использовать [точку останова в функции](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Управление точками останова и их отслеживание

Используйте окно **Точки останова**. Дополнительные сведения см. в разделе [Управление точками останова](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Приостановка кода и отладка при возникновении определенного обработанного или необработанного исключения

Хотя помощник по исправлению ошибок показывает, где произошла ошибка, если вы хотите приостановить выполнение и отладить конкретную ошибку, можно [велеть отладчику прервать выполнение при возникновении исключения](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Задание точки останова из стека вызовов

Если вы хотите приостановить и отладить код при проверке потока выполнения или просмотре функций в окнах **стека вызовов**, см. раздел [Задание точки останова в окне стека вызовов](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Приостановка кода в указанной инструкции сборки

Это можно сделать, [задав точку останова в окне дизассемблирования](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Выполнение кода

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Использование команд для пошагового выполнения кода во время отладки

Дополнительные сведения см. в разделе [Навигация по коду с помощью отладчика](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Проверка данных

### <a name="check-the-value-of-variables-while-running-your-app"></a>Проверка значений переменных во время выполнения приложения

Наведите указатель мыши на переменные, используя [подсказки по данным](view-data-values-in-data-tips-in-the-code-editor.md), или [проверьте переменные в окне видимых и локальных переменных](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Наблюдение за изменением значения конкретной переменной

Установите контрольное значение для переменной. Дополнительные сведения см. в разделе [Установка контрольных значений для переменных](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Просмотр слишком длинных строк для окна отладчика

Откройте встроенный [визуализатор строк](view-strings-visualizer.md) во время отладки.

## <a name="configure-debugging"></a>Настройка отладки

### <a name="customize-information-shown-in-the-debugger"></a>Настройка сведений, отображаемых в отладчике

Вам может потребоваться отобразить сведения, отличные от типа объекта, в качестве значения в различных окнах отладчика. Для кода C#, Visual Basic, F#, и C++/CLI используйте атрибут [DebuggerDisplay](using-the-debuggerdisplay-attribute.md). Для более сложных вариантов можно также настроить пользовательский интерфейс, создав [пользовательский визуализатор](create-custom-visualizers-of-data.md).

Для машинного кода C++ используйте [платформу NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Настройка параметров отладчика

Сведения о настройке параметров отладчика и параметров проекта отладчика см. в разделе [Параметры отладчика и подготовка](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Дополнительные задачи

### <a name="fix-an-exception"></a>Исправление исключения

См. раздел [Исправление исключения](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Изменение кода во время сеанса отладки

Используйте функцию [Изменить и продолжить](edit-and-continue.md). Для XAML используйте [Горячую перезагрузку XAML](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Отправка сообщений в окно вывода без изменения кода

Задайте точку трассировки. Дополнительные сведения см. в разделе [Использование точек трассировки](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Просмотр порядка, в котором вызываются функции

См. раздел [Просмотр стека вызовов](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Отладка на удаленных компьютерах

См. раздел [Удаленная отладка](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Отладка уже запущенного приложения

См. раздел [Присоединение к выполняемому процессу](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Отладка многопоточных приложений

См. раздел [Отладка многопоточных приложений](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Исправление проблем производительности

См. раздел [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md).