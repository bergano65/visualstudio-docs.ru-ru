---
title: Поиск задачи отладки
description: Определить функцию отладчика, которая поможет вам отладить приложение
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
ms.openlocfilehash: a4667fc630d86691d95e9dc9cd205b29f7b0f525
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349711"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Поиск задачи отладки в Visual Studio

Если вам нужна помощь по сопоставлению задачи отладки с соответствующей функцией отладчика Visual Studio, используйте ссылки, приведенные в этой статье. Список задач содержит распространенные задачи, такие как приостановка кода для отладки, Проверка переменных и отправка сообщений в окно **вывода** . Если вам нужны общие сведения о функциях отладчика, см. статью [Знакомство](debugger-feature-tour.md) с отладчиком.

## <a name="pause-running-code"></a>Приостановить выполнение кода

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Приостановка выполнения кода для проверки строки кода, которая может содержать ошибку

Задайте точку останова. Для получения дополнительной информации см. раздел [Использование точек останова](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Приостановка и проверка приложения при достижении определенного состояния

Используйте условную точку останова, чтобы управлять тем, где и когда точка останова активируется с помощью условной логики. Дополнительные сведения см. в разделе [условия точки останова](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Приостанавливать код только при изменении свойства или значения конкретного объекта

Для C++задайте [точку останова в данных](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
Для приложений, использующих .NET Core 3, можно также задать [точку останова по данным](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

В противном C# случае F# , только для и можно [отвести идентификатор объекта с условной точкой останова](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Приостановить код внутри цикла в определенной итерации

Установите точку останова, используя **количество попаданий** в качестве условия. Дополнительные сведения см. в разделе [число попаданий](using-breakpoints.md#hit-count).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Приостановить код в начале функции, если известно имя функции, но не ее расположение

Это можно сделать с помощью точки останова функции. Дополнительные сведения см. в разделе [Задание точек останова для функций](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Управляйте точками останова и следите за ними

Используйте окно **точки останова** . Дополнительные сведения см. в разделе [Управление точками останова](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Приостановить код и отладку при возникновении определенного обработанного или необработанного исключения

Несмотря на то, что в вспомогательном приложении об исключении показано, где произошла ошибка, если вы хотите приостановить и отладить конкретную ошибку, можно [указать отладчику прерывать работу при](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)возникновении исключения.

### <a name="set-a-breakpoint-from-the-call-stack"></a>Установка точки останова из стека вызовов

Если вы хотите приостановить и отладить код при проверке последовательности выполнения или просмотре функций в окнах **стека вызовов** , см. раздел [Установка точки останова в окне Стек вызовов](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Приостановить код в указанной инструкции сборки

Это можно сделать, [установив точку останова в окне дизассемблирования](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Выполнить код

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Сведения о командах для пошагового выполнения кода во время отладки

Дополнительные сведения см. [в разделе Навигация по коду с помощью отладчика](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Проверка данных

### <a name="check-the-value-of-variables-while-running-your-app"></a>Проверка значений переменных во время выполнения приложения

Наведите указатель мыши на переменные, используя [Советы по данным](view-data-values-in-data-tips-in-the-code-editor.md) или [Изучите переменные в окне видимые и локальные](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Наблюдение за изменением значения определенной переменной

Задайте контрольное значение для переменной. Дополнительные сведения см. в разделе [установка контрольного значения для переменных](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Просмотр слишком длинных строк для окна отладчика

Откройте встроенный [Визуализатор строк](view-strings-visualizer.md) во время отладки.

## <a name="configure-debugging"></a>Настройка отладки

### <a name="customize-information-shown-in-the-debugger"></a>Настройка сведений, отображаемых в отладчике

Может потребоваться отобразить сведения, отличные от типа объекта, в качестве значения в различных окнах отладчика. Для C#кода, Visual Basic F#, и C++/CLI используйте атрибут [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Для более сложных параметров можно также настроить пользовательский интерфейс, создав [Пользовательский визуализатор](create-custom-visualizers-of-data.md).

Для машинного кода C++используйте [платформу NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Настройка параметров отладчика

Сведения о настройке параметров отладчика и параметров проекта отладчика см. в разделе [параметры отладчика и подготовка](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Дополнительные задачи

### <a name="edit-code-during-a-debugging-session"></a>Изменение кода во время сеанса отладки

Используйте ["изменить и продолжить"](edit-and-continue.md). Для XAML используйте [горячую перезагрузку XAML](xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Отправка сообщений в окно вывода без изменения кода

Задайте точку трассировки. Дополнительные сведения см. [в разделе Использование точек отслеживания](using-tracepoints.md).

### <a name="debug-on-remote-machines"></a>Отладка на удаленных компьютерах

См. раздел [Удаленная отладка](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Отладка уже запущенного приложения

См. раздел [Подключение к запущенным процессам](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Отладка многопоточных приложений

См. раздел [Отладка многопоточных приложений](debug-multithreaded-applications-in-visual-studio.md).