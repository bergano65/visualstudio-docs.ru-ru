---
title: Возможности IntelliTrace | Документация Майкрософт
description: Сведения о возможностях IntelliTrace в Visual Studio. Функция IntelliTrace используется для записи событий и вызовов методов в приложении.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4c974b9056b41de2e021f5918963d1d28ffa3db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905001"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>Возможности IntelliTrace (C#, Visual Basic, C++)

IntelliTrace можно использовать для записи событий и вызовов методов, что позволяет проверять состояние приложения (стек вызовов и значения локальных переменных) на различных этапах выполнения. Просто запустите отладку обычным образом — средство IntelliTrace включено по умолчанию — и просматривайте данные, записываемые IntelliTrace в новом окне **Средства диагностики** на вкладке **События**. Выберите событие и щелкните **Активировать журнал отладки**, чтобы увидеть стек вызовов и локальные переменные, записанные для этого события.

Пошаговое описание см. в [пошаговом руководстве по использованию IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

Средство IntelliTrace доступно в выпуске Visual Studio Enterprise, но не в выпусках Visual Studio Professional или Community.

Чтобы убедиться, что средство IntelliTrace включено, откройте страницу параметров, последовательно выбрав **Сервис > Параметры > IntelliTrace**. Параметр **Включить IntelliTrace** должен быть выбран по умолчанию.

> [!NOTE]
> Все параметры на странице параметров **IntelliTrace** охватывают Visual Studio как единое целое, а не распространяются на отдельные проекты или решения. Изменение этих параметров применяется ко всем экземплярам Visual Studio, всем сеансам отладки и всем проектам и решениям.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a> Выбор событий, записываемых IntelliTrace (C#, Visual Basic)

Можно включить или отключить запись определенных событий IntelliTrace.

Если выполняется отладка, остановите ее. Последовательно выберите элементы **Сервис > Параметры > IntelliTrace > События IntelliTrace**. Выберите события, которые будет записывать IntelliTrace.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a> Сбор моментальных снимков (C#, Visual Basic, C++)

Этот параметр не включен по умолчанию, но IntelliTrace может сохранять моментальные снимки приложения при каждом событии точки останова и шага отладчика, а также поддерживает сеанс исторической отладки для просмотра этих моментальных снимков. Моментальный снимок предоставляет полную информацию о состоянии приложения. Чтобы включить сбор моментальных снимков последовательно щелкните элементы **Сервис > Параметры > IntelliTrace > Общие**, затем установите флажок **IntelliTrace snapshots (managed and native)** (Моментальные снимки IntelliTrace (управляемый и машинный код)). Дополнительные сведения см. в разделе [Проверка предыдущих состояний приложения с помощью IntelliTrace](../debugger/view-historical-application-state.md).

Моментальные снимки доступны в Visual Studio Enterprise 2017 версии 15.5 и более поздних версий. Для использования этой функции требуется установка Windows 10 Anniversary Update или более поздней версии.  Для приложений .NET Core и ASP.NET Core требуется Visual Studio Enterprise 2017 версии 15.7. Для собственных приложений для Windows требуется Visual Studio Enterprise 2017 версии 15.9 (предварительная версия 2).

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a> Сбор событий IntelliTrace и сведений о вызовах (C#, Visual Basic)

Эта возможность не включена по умолчанию, но IntelliTrace может записывать вызовы методов вместе с событиями. Чтобы включить сбор вызовов методов, последовательно щелкните элементы **Сервис > Параметры > IntelliTrace > Общие**, затем установите флажок **IntelliTrace events and call information (managed only)** (События IntelliTrace и данные о вызовах (только управляемый код)).

На данный момент сведения о вызовах не поддерживаются для приложений C++ и ASP.NET Core.

Это позволит увидеть журнал стека вызовов и переходить по вызовам в вашем коде. IntelliTrace записывает такие данные, как имена методов, точки входа и выхода методов и определенные значения параметров, а также возвращаемые значения.

> [!TIP]
> Этот параметр не включен по умолчанию, поскольку он связан со значительными издержками. IntelliTrace позволяет не только перехватывать каждый вызов метода, осуществляемый приложением, но и обрабатывать наборы данных значительного размера в случае необходимости их отображения на экране или сохранения на диск.
>
> Чтобы снизить издержки на производительность, можно ограничить список событий, записываемых IntelliTrace, и поддерживать минимальное количество собираемых модулей. Дополнительные сведения см. в разделе [Управление объемом сведений о вызовах, записываемых IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Использование области навигации

Можно использовать области навигации, которая отображается слева от окна кода. Если область навигации отсутствует, последовательно выберите **Сервис > Параметры > IntelliTrace > Дополнительно** и выберите параметр **Отображать область навигации в режиме отладки**.

В области навигации в режиме отладки с ведением журнала можно перемещаться вперед и назад по вызовам методов и событиям. Дополнительные сведения об отладке с ведением журнала см. в разделе [Отладка с ведением журнала](../debugger/historical-debugging.md). Здесь доступен ряд команд.

|Команда|Описание|
|-|-|
|**Задать контекст отладчика здесь**|Задает контексту отладки временной интервал вызова, в котором он отображается.<br /><br /> Значок отображается только на текущем стеке вызовов.|
|**Возврат к месту вызова**|Перемещает указатель и контекст отладки назад в тот момент, где была вызвана текущая функция.<br /><br /> Если вы находитесь в динамическом режиме отладки, эта команда включает отладку с ведением журнала. Если перейти в исходное место прерывания выполнения, отладка с ведением журнала отключается и включается режим динамической отладки.|
|**Перейти к предыдущему вызову или событию IntelliTrace**|Перемещает указатель и контекст отладки назад к предыдущему вызову или событию.<br /><br /> Если вы находитесь в динамическом режиме отладки, эта команда включает отладку с ведением журнала.|
|**Шаг с заходом**|Выполняет шаг с заходом в текущую выбранную функцию.<br /><br /> Эта команда доступна только в режиме отладки с ведением журнала.|
|**Перейти к следующему вызову или событию IntelliTrace**|Перемещает указатель и контекст отладки к следующему вызову или событию, для которого имеются данные IntelliTrace.<br /><br /> Эта команда доступна только в режиме отладки с ведением журнала.|
|**Перейти в динамический режим**|Возврат в динамический режим отладки.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Найти строку или метод в IntelliTrace

Поиск методов можно осуществлять только в том случае, если были включены сведения о вызовах метода. Можно выполнить поиск конкретной строки или метода в журнале IntelliTrace. Во время приостановки выполнения отладчика щелкните правой кнопкой мыши в теле функции, чтобы открыть контекстное меню, и выберите **Найти эту строку в IntelliTrace** или **Найти этот метод в IntelliTrace**.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a> Управление объемом сведений о вызовах, записываемых IntelliTrace

По умолчанию IntelliTrace записывает сведения для всех модулей, используемых в решении. IntelliTrace можно настроить для записи сведений о вызовах только в представляющих интерес модулях. Выбрав **Сервис > Параметры > IntelliTrace > Модули**, можно указать модули, включаемые в сбор данных IntelliTrace или исключаемые из него. IntelliTrace будет собирать только события, источниками которых являются указанные модули, и вызовы методов, выполненные в представляющих интерес модулях.

Чтобы добавить несколько модулей, используйте подстановочный знак * в начале или конце строки. В качестве имени модуля используйте имя файла, а не имя сборки. Пути к файлам не принимаются.

Попытайтесь свести число модулей к минимуму. Поскольку в этом случае уменьшается объем собираемых данных, уровень производительности повышается. Кроме того, в пользовательском интерфейсе снижается уровень шума.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a> Сохранение данных IntelliTrace в файл (C#, Visual Basic, C++)

Во время отладки и пока приложение находится в состоянии приостановки, можно сохранить данные, собранные IntelliTrace, выбрав **Отладка > IntelliTrace > Сохранение сеанса IntelliTrace**. Если приложение все еще выполняется или отладка остановлена, пункт меню будет отключен и сохранить данные, собранные IntelliTrace, будет невозможно.

IntelliTrace можно настроить для автоматического сохранения в файл, последовательно выбрав **Сервис > Параметры > IntelliTrace > Дополнительно** и выбрав параметр **Хранить записи IntelliTrace в этом каталоге**. Можно также настроить размер набора для созданного файла, по достижении которого IntelliTrace перезаписывает старые данные при нехватке свободного пространства. Visual Studio создает два файла для каждого сеанса IntelliTrace, если файлы сохраняются автоматически и процесс размещения Visual Studio (vshost.exe) включен.

> [!TIP]
> Для экономии места на диске отключите автоматическое сохранение файлов, когда они больше не нужны. Существующие файлы не удалятся. Всегда можно сохранить файл по запросу из контекстного меню.

При сохранении данных IntelliTrace в файл вы получаете один ITRACE-файл для каждого процесса, из которого IntelliTrace собрал данные. ITRACE-файл можно открыть в Visual Studio, выбрав **Файл > Открыть > Файл** и выбрав ITRACE-файл в диалоговом окне "Открытие файла". Дополнительные сведения см. в разделе [Использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Блоги

[IntelliTrace в Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Пошаговое руководство по отладке в реальном времени с использованием IntelliTrace в Visual Studio 2015 (текстовый редактор)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Пошаговое руководство по отладке в реальном времени с использованием IntelliTrace в Visual Studio 2015 (социальный клуб)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[IntelliTrace в Visual Studio Enterprise 2015 теперь поддерживает вложение](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[Сбор данных из службы Windows с помощью автономного сборщика данных IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[Редактирование плана коллекции IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[Пользовательские TraceSource и отладка с помощью IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[Выполнение автономного сборщика и пулов приложений IntelliTrace с использованием учетных записей Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Форумы

[Отладчик Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>Видеоролики

[Взаимодействие с IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Отладка с ведением журнала с помощью IntelliTrace в Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
