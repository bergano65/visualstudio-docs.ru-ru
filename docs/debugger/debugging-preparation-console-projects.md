---
title: Подготовка к отладке проектов консоли | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be22786a78c16dc9ffa05aba38075e4762485d2d
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533316"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Подготовка к отладке: Консольные проектыC#( C++,, Visual Basic F#,)

Подготовка к отладке консольного проекта аналогична подготовке к отладке проекта Windows с некоторыми дополнительными соображениями, такими как установка аргументов командной строки и приостановка приложения для отладки. Дополнительные сведения см. в разделе [Windows Forms приложения](../debugger/debugging-preparation-windows-forms-applications.md)и [подготовка к отладке: Windows Forms приложения (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Из-за схожести всех консольных приложений в этом разделе описываются следующие типы проектов:

- C#, Visual Basic и F# консольное приложение

- консольное приложение C++ (.NET);

- консольное приложение С++ (Win32).

  Консольное приложение использует окно **Консоль** для получения входных данных и отображения выходных сообщений. Для записи в окно **консоли** приложение должно использовать объект **Console** вместо объекта Debug. Для записи в окно **Вывод Visual Studio** используется, как обычно, объект Debug. Необходимо убедиться в какое место приложение записывает данные, иначе может оказаться, что поиск сообщений ведется не в том месте. Дополнительные сведения см. в разделах [Класс Console](/dotnet/api/system.console), [Класс Debug](/dotnet/api/system.diagnostics.debug) и [Окно вывода](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Задание аргументов командной строки

Может потребоваться задание аргументов командной строки для консольного приложения. Дополнительные сведения см. в разделе [Параметры проекта для C++ конфигурации отладки](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Параметры проекта для Visual Basic конфигурации отладки](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)или [Параметры проекта для C# конфигураций отладки](../debugger/project-settings-for-csharp-debug-configurations.md).

Подобно всем свойствам проекта, эти аргументы сохраняются в интервале между сеансами (как отладки, так и Visual Studio). Поэтому необходимо учитывать, что если предыдущий сеанс был посвящен отладке консольного приложения, в диалоговом окне **Страницы свойств \<проект>** могут присутствовать аргументы, сохранившиеся от предыдущих сеансов отладки.

## <a name="start-the-application"></a>Запуск приложения

 Некоторые консольные приложения после запуска выполняются до полного завершения, после чего сразу закрываются. Если это происходит быстро, то можно не успеть прервать выполнение приложения и выполнить отладку. Чтобы можно было выполнить отладку такого приложения, необходимо использовать один из следующих приемов для запуска приложения.

- Установите точку останова в коде и запустите приложение.

- Запустите приложение с помощью **клавиши F10** (**Отладка** >  > **шаг**с обходом) или **F11** (шаг с заходом**в**начало), а затем просмотрите код, используя другие параметры, такие как **Запуск для щелчка**.

- В редакторе кода щелкните правой кнопкой мыши строку и выберите команду **выполнить до текущей позиции**.

  При отладке консольного приложения может потребоваться запуск приложения из командной строки, а не из Visual Studio. В этом случае можно запустить приложение из командной строки и присоединить к нему отладчик Visual Studio. Дополнительные сведения см. [в разделе Присоединение к запущенным процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  При запуске консольного приложения из Visual Studio окно **Консоль** иногда отображается позади окна Visual Studio. Если при попытке запустить консольное приложение из Visual Studio кажется, что ничего не происходит, попробуйте переместить окно Visual Studio.

## <a name="see-also"></a>См. также
- [Отладка машинного кода](../debugger/debugging-native-code.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
- [Типы проектов Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Безопасность отладчика](../debugger/debugger-security.md)