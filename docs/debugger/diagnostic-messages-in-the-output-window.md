---
title: Отправка сообщений в окно вывода | Документация Майкрософт
description: Запись сообщений во время выполнения в окно "Вывод" в Visual Studio с помощью класса Debug или Trace, которые входят в библиотеку классов System.Diagnostics.
ms.custom: SEO-VS-2020
ms.date: 11/08/2018
ms.topic: how-to
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b61d0c6bc89f8be2680930411e0b9109fdeec473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872060"
---
# <a name="send-messages-to-the-output-window"></a>Отправка сообщений в окно "Вывод"

Во время выполнения сообщения в **окне вывода** можно написать с помощью класса <xref:System.Diagnostics.Debug> или <xref:System.Diagnostics.Trace>; оба класса входят в библиотеку классов <xref:System.Diagnostics>. Класс <xref:System.Diagnostics.Debug> используется, если необходимо выводить сообщение только в *отладочной* версии программы. Класс <xref:System.Diagnostics.Trace> используется в том случае, если необходимо выводить сообщение и в *отладочной* версии программы, и в *выпускаемой*.

## <a name="output-methods"></a>Методы вывода
 Классы <xref:System.Diagnostics.Trace> и <xref:System.Diagnostics.Debug> предоставляют следующие методы вывода:

- Различные методы `Write`, которые выводят сведения без прерывания выполнения программы. Эти методы заменяют метод `Debug.Print`, который использовался в предыдущих версиях Visual Basic.

- Методы <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, которые прерывают выполнение программы и выводят сведения, если заданное условие не выполняется. По умолчанию метод `Assert` отображает сведения в диалоговом окне. Дополнительные сведения см. в разделе [Утверждения в управляемом коде](../debugger/assertions-in-managed-code.md).

- Методы <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, которые всегда прерывают выполнение программы и выводят сведения. По умолчанию методы `Fail` отображают сведения в диалоговом окне.

В окне **вывода** также могут отображаться сведения о следующем:

- Загруженные или выгруженные модули отладчика.

- Вызванные исключения.

- Завершившиеся процессы.

- Завершившиеся потоки.

## <a name="see-also"></a>См. также
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Окно вывода](../ide/reference/output-window.md)
- [Трассировка и инструментирование приложений](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
