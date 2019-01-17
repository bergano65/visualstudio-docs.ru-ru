---
title: Отправлять сообщения в окне вывода | Документация Майкрософт
ms.date: 11/08/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18ea526fdff312ce46cdb63b6c74e0e0a2600116
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906752"
---
# <a name="send-messages-to-the-output-window"></a>Отправка сообщений в окно "Вывод"

Можно написать сообщения времени выполнения для **вывода** окна с помощью <xref:System.Diagnostics.Debug> класса или <xref:System.Diagnostics.Trace> класса, которые являются частью из <xref:System.Diagnostics> библиотеки классов. Используйте <xref:System.Diagnostics.Debug> , если необходимо выводить сообщение только *Отладка* версии программы. Используйте <xref:System.Diagnostics.Trace> , если необходимо выводить сообщение в обоих *Отладка* и *выпуска* версий.  
  
## <a name="output-methods"></a>Методы вывода  
 Классы <xref:System.Diagnostics.Trace> и <xref:System.Diagnostics.Debug> предоставляют следующие методы вывода:  
  
- Различные методы `Write`, которые выводят сведения без прерывания выполнения программы. Эти методы заменяют метод `Debug.Print`, который использовался в предыдущих версиях Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> методы, которые приостанавливают выполнение и выходные данные сведения, если заданное условие не выполняется. По умолчанию метод `Assert` отображает сведения в диалоговом окне. Дополнительные сведения см. в разделе [Утверждения в управляемом коде](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> И <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> методы, которые всегда выделить сведения о выполнении и выходных данных. По умолчанию методы `Fail` отображают сведения в диалоговом окне.  
  
**Вывода** окно также можно отображать сведения о:  
  
- Загруженные или выгруженные модули отладчика.  
  
- Вызванные исключения.  
  
- Завершившиеся процессы.  
  
- Завершившиеся потоки.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Окно выходных данных](../ide/reference/output-window.md)   
 [Трассировка и инструментирование приложений](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
