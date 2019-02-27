---
title: Отладка управляемого кода | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 14dc53413f646718b85ec9ea43d968dc9f64a96f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719328"
---
# <a name="debugging-managed-code"></a>Отладка управляемого кода

В данном разделе приводится описание общих проблем отладки и способов их решения для управляемых приложений или приложений, написанных на языках, предназначенных для общеязыковой среды выполнения, например Visual Basic, C#, и C++). Описанные здесь методики — методики высшего уровня. [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>В этом разделе

[Диагностические сообщения в окне вывода](../debugger/diagnostic-messages-in-the-output-window.md) описывает <xref:System.Diagnostics.Debug> и <xref:System.Diagnostics.Trace> классы, с помощью которых можно написать сообщения времени выполнения для **вывода** окна. Эти классы содержат методы вывода, позволяющие выводить сведения без прерывания выполнения программы, и выводить сведения, которые также прерывают выполнение при невыполнении заданного условия.

[Утверждения в управляемом коде](../debugger/assertions-in-managed-code.md) описывает утверждения в управляемом коде, которые проверяют условия, заданные в качестве аргументов `Assert` методы. Кроме того, этот раздел содержит пример кода, содержащий сведения об использовании методов классов <xref:System.Diagnostics.Debug> и <xref:System.Diagnostics.Trace>, вопросы, касающиеся отладочной и выпускаемой версий кода, побочных эффектов, аргументов утверждений, настройки поведения утверждений и файлов конфигурации.

[Оператор Stop в Visual Basic](../debugger/stop-statements-in-visual-basic.md) описывает `Stop` инструкцию, которая представляет собой альтернативу указанию точки останова. Кроме того, раздел содержит пример кода и сравнение оператора `Stop` с оператором `End`, а также оператора `Stop` с оператором `Assert`.

[Пошаговое руководство: Отладка в Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md) пошаговые инструкции по созданию формы Windows и ее отладке. Форма Windows Forms - стандартный компонент приложения Windows, — один из наиболее распространенных вариантов управляемых приложений. В данном пошаговом руководстве используются языки Visual C# и Visual Basic, но методика создания форм Windows Forms с помощью C++ во многом аналогична.

[Отладка метода OnStart](../debugger/how-to-debug-the-onstart-method.md) содержатся примеры кода, чтобы можно было отлаживать `OnStart` метод управляемой службы Windows. Для отладки метода `OnStart` службы Windows необходимо добавить несколько строк кода для имитации работы службы.

[Отладка в смешанном режиме](../debugger/debugging-mixed-mode-applications.md) Описание отладки приложений в смешанном режиме. Это подразумевает любое приложение, объединяющее машинный код с управляемым кодом.

[Ошибка: Отладка невозможна, поскольку в системе включен отладчик ядра](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) описание сообщения об ошибке, возникающее при попытке произвести отладку управляемого кода на [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], или система Windows NT которая была запущена в режиме отладки.

[JIT-оптимизацию и отладка](../debugger/jit-optimization-and-debugging.md) описываются последствия JIT-оптимизацию на отладку.

[Отладка LINQ и DLINQ](../debugger/debugging-linq.md) описывает методы отладки LINQ запросов.

[Пошаговое руководство: Отладка параллельного приложения](../debugger/walkthrough-debugging-a-parallel-application.md) описывается использование **параллельных задач** и **Параллельные стеки** средство windows для отладки параллельного приложения.

## <a name="related-sections"></a>Связанные разделы

[IntelliTrace](../debugger/intellitrace.md) поиска ошибок быстрее и проще, путем записи журнала выполнения приложения с помощью IntelliTrace. Перемещайтесь вперед или назад между различными записанными событиями и вызовами для определения состояния приложения в соответствующие моменты времени. Производите отладку приложения, не устанавливая множество точек останова и не перезапуская приложение слишком часто. Требуется Visual Studio Enterprise.

[Трассировка и инструментирование приложений](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) описание трассировки приложений, позволяет наблюдать за выполнением приложения во время и инструментирования приложений, размещающего операторы трассировки в стратегически важных местах кода. Кроме того, в данном разделе представлены ссылки на руководство по оборудованию и трассировке, а также по переключателям трассировки, слушателям трассировки, коду трассировки в приложении, добавлению оператора трассировки в код приложения и условной компиляции с использованием атрибутов <xref:System.Diagnostics.Debug> и <xref:System.Diagnostics.Trace>.

[/ ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) описание параметра компоновщика, который добавляет <xref:System.Diagnostics.DebuggableAttribute> в код, написанный на языке C++. Этот атрибут необходим для использования таких функций отладчика, как, например, "присоединить с C++".

[Отладка приложений служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) рекомендации по отладке служебных приложений Windows, включая настройку, присоединения к процессу, отладку кода в службы `OnStart` метод и код в методе Main метод, задание точек останова и использование диспетчера управления службами для запуска, остановки, приостановки и продолжения работы служб.

[Отладка и профилирование](/dotnet/framework/debug-trace-profile/index) рассматриваются требования к конфигурации и отладки приложений .NET Framework.

[Отладка приложений скриптов и веб-приложений](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) описывает распространенные отладки проблем и методов, которые могут возникнуть при отладке скрипта и веб-приложений.

[Новые возможности отладчика в Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md) Описание новых возможностей отладки, добавленных в этом выпуске [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Домашняя страница отладки](../debugger/debugger-feature-tour.md) ссылки на крупные разделы документации об отладке. В них содержатся следующие сведения: новые возможности отладчика, сведения о параметрах и подготовке, точках останова, обработке исключений, изменении и продолжении выполнения, отладке управляемого кода, проектов Visual C++, объектов COM и ActiveX, библиотек DLL, SQL, а также ссылки на пользовательский интерфейс.

## <a name="see-also"></a>См. также

[Пошаговое руководство: Отладка пользовательских Windows Forms элементы управления во время разработки](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[безопасность отладчика](../debugger/debugger-security.md)
[отладки в Visual Studio](../debugger/index.md) 
 [ Сначала посмотрим, отладчик](../debugger/debugger-feature-tour.md)