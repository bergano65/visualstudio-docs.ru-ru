---
title: Отправка сообщений в окно вывода | Документация Майкрософт
ms.date: 11/08/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b563f58d08a732ec224bb8bbf47ad807c4e81d
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605379"
---
# <a name="send-messages-to-the-output-window"></a>Отправка сообщений в окно "Вывод"

Сообщения времени выполнения можно записывать в окно **вывода** с помощью <xref:System.Diagnostics.Debug> класса или <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> класса, которые являются частью библиотеки классов. Используйте класс <xref:System.Diagnostics.Debug> , если требуется только вывод в отладочной  версии программы. Используйте класс <xref:System.Diagnostics.Trace> , если требуется вывод как в отладочной  , так и в *окончательной* версиях.

## <a name="output-methods"></a>Методы вывода
 Классы <xref:System.Diagnostics.Trace> и <xref:System.Diagnostics.Debug> предоставляют следующие методы вывода:

- Различные методы `Write`, которые выводят сведения без прерывания выполнения программы. Эти методы заменяют метод `Debug.Print`, который использовался в предыдущих версиях Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>методы <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> и, которые нарушают выполнение и выходные данные при сбое указанного условия. По умолчанию метод `Assert` отображает сведения в диалоговом окне. Дополнительные сведения см. в разделе [Утверждения в управляемом коде](../debugger/assertions-in-managed-code.md).

- Методы <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> и<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> , которые всегда нарушают выполнение и выходные данные. По умолчанию методы `Fail` отображают сведения в диалоговом окне.

Окно **вывод** может также отображать сведения о:

- Загруженные или выгруженные модули отладчика.

- Вызванные исключения.

- Завершившиеся процессы.

- Завершившиеся потоки.

## <a name="see-also"></a>См. также
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Окно вывода](../ide/reference/output-window.md)
- [Приложения для трассировки и инструментирования](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
