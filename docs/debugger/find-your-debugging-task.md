---
title: Поиск задачи отладки
description: Определите функцию отладчика, которая поможет вам отладить приложение
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
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301149"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Найдите задачу отладки в Visual Studio

Если вам нужна помощь, чтобы сопоставить задачу отладки с правильной функцией отладчика Visual Studio, которая имеет отношение, используйте ссылки, приведенные в этой статье. Список задач здесь включает в себя общие задачи, такие как приостановка кода для отладки, проверка переменных и отправка сообщений в окно **вывода.** Если вам нужен обзор функций отладчика, смотрите [сначала посмотреть на отладчик вместо](debugger-feature-tour.md) этого.

## <a name="pause-running-code"></a>Приостановка работы кода

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Приостановить запуск кода для проверки строки кода, которая может содержать ошибку

Задайте точку останова. Для получения дополнительной информации [см.](using-breakpoints.md)

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Пауза и проверка приложения, когда оно достигнет определенного состояния

Попробуйте условную точку разрыва, чтобы контролировать, где и когда точка разрыва активируется с помощью условной логики. Для получения дополнительной информации [см.](using-breakpoints.md#breakpoint-conditions)

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Приостановка кода только в том случае, если изменяется свойство или значение определенного объекта

Для СЗ установите [точку разрыва данных.](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus) 
::: moniker range=">= vs-2019"
Для приложений, использующих .NET Core 3, можно также установить [точку разрыва данных.](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)
::: moniker-end

В противном случае, только для C и F, вы можете [отслеживать идентификатор объекта с помощью условной точки разрыва.](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Пауза код внутри цикла на определенной итерации

Установите точку разрыва, используя **количество хитов** в качестве условия. Для получения дополнительной информации [см.](using-breakpoints.md#set-a-hit-count-condition)

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Приостановить код в начале функции, когда вы знаете имя функции, но не его местоположение

Это можно сделать с точки разрыва функции. Для получения дополнительной информации [см.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Приостановить код в начале нескольких функций с тем же именем

Если у вас есть несколько функций с тем же именем (перегруженные функции или функции в различных проектах), можно использовать [точку разрыва функции.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Управление и отслеживание моментов разрыва

Используйте окно **Breakpoints.** Для получения дополнительной информации [см.](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Приостановить код и отладить, когда выбрасывается определенное обработанное или необработанное исключение

Хотя Помощник исключения показывает, где произошла ошибка, если вы хотите приостановить и отладить конкретную ошибку, вы можете [сказать отладчику, чтобы он сломался при броске исключения.](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)

### <a name="set-a-breakpoint-from-the-call-stack"></a>Установите точку разрыва из стека вызовов

Если вы хотите приостановить и отладить код при изучении потока выполнения или функций просмотра в окнах **Call Stack,** см. [Установить точку разрыва в окне стека вызова.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Приостановка кода при определенной инструкции сборки

Это можно сделать, [установив точку разрыва из окна разборки.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

## <a name="execute-code"></a>Выполнение кода

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Изучите команды, чтобы пройти через код во время отладки

Для получения дополнительной информации [см.](navigating-through-code-with-the-debugger.md)

## <a name="inspect-data"></a>Данные проверки

### <a name="check-the-value-of-variables-while-running-your-app"></a>Проверьте значение переменных во время работы приложения

Нависает над переменными, используя [советы по данным](view-data-values-in-data-tips-in-the-code-editor.md) или [проверяйте переменные в окне Autos and Locals.](autos-and-locals-windows.md)

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Обратите внимание на изменение значения конкретной переменной

Установите часы на переменной. Для получения дополнительной [информации см.](watch-and-quickwatch-windows.md)

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Просмотр строк, которые слишком длинны для окна отладчика

Откройте встроенный [визуализатор строки](view-strings-visualizer.md) во время отладки.

## <a name="configure-debugging"></a>Настройка отладки

### <a name="customize-information-shown-in-the-debugger"></a>Настройка информации, отображаемая в отладчике

Вы можете показать информацию, кроме типа объекта, как значение в различных окнах отладчика. Для кода СИ, Visual Basic, F и C'/CLI используйте атрибут [DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Для более продвинутых опций можно также настроить пользовательский пользовательский пользовательский пользовательский [визуализатор.](create-custom-visualizers-of-data.md)

Для наиболее родного КЗ используйте [фреймворк NatVis.](create-custom-views-of-native-objects.md)

### <a name="configure-debugger-settings"></a>Настройка настроек отладчика

Для настройки параметров отладчика и настройки проекта отваживают [настройки и подготовки Debugger.](debugger-settings-and-preparation.md)

## <a name="additional-tasks"></a>Дополнительные задачи

### <a name="fix-an-exception"></a>Исправление исключения

См [Исключите исключение](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Отодевание кода во время сеанса отладки

Используйте [edit и продолжайте](edit-and-continue.md). Для XAML используйте [XAML Hot Reload.](../xaml-tools/xaml-hot-reload.md)

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Отправка сообщений в окно вывода без изменения кода

Установите точку трассировки. Для получения дополнительной информации [см.](using-tracepoints.md)

## <a name="view-the-order-in-which-functions-are-called"></a>Просмотр порядка, в котором вызываются функции

[Узнайте, как просмотреть стек вызова.](how-to-use-the-call-stack-window.md)

### <a name="debug-on-remote-machines"></a>Отошибока на удаленных машинах

См. раздел [Удаленная отладка](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Отогладить приложение, которое уже запущено

См [Прикрепите к запущенным процессам.](attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="debug-multithreaded-applications"></a>Отладка многопоточных приложений

Посмотреть [отожобите многопоточные приложения.](debug-multithreaded-applications-in-visual-studio.md)

### <a name="fix-performance-issues"></a>Исправление проблем производительности

Смотрите [первый взгляд на инструменты профилирования](../profiling/profiling-feature-tour.md)