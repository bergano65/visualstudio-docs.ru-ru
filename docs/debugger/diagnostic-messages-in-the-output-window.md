---
title: Отправлять диагностические сообщения в окне вывода | Документация Майкрософт
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 27cec31b775ba5f8d201c81cbd65f5b161353986
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252301"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Отправлять диагностические сообщения в окне вывода
Можно написать сообщения времени выполнения для **вывода** окна с помощью <xref:System.Diagnostics.Debug> класса или <xref:System.Diagnostics.Trace> класса, которые являются частью из <xref:System.Diagnostics> библиотеки классов. Используйте <xref:System.Diagnostics.Debug> , если необходимо выводить сообщение только в *Отладка* версии программы. Используйте <xref:System.Diagnostics.Trace> , если необходимо выводить сообщение в обоих *Отладка* и *выпуска* версий.  
  
## <a name="output-methods"></a>Методы вывода  
 Классы <xref:System.Diagnostics.Trace> и <xref:System.Diagnostics.Debug> предоставляют следующие методы вывода:  
  
-   Различные методы `Write`, которые выводят сведения без прерывания выполнения программы. Эти методы заменяют метод `Debug.Print`, который использовался в предыдущих версиях Visual Basic.  
  
-   Методы <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, которые прерывают выполнение программы и выводят сведения, если заданное условие не выполняется. По умолчанию метод `Assert` отображает сведения в диалоговом окне. Дополнительные сведения см. в разделе [утверждения в управляемом коде](../debugger/assertions-in-managed-code.md).  
  
-   Методы <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, которые всегда прерывают выполнение программы и выводят сведения. По умолчанию методы `Fail` отображают сведения в диалоговом окне.  
  
 В дополнение к программному выводу приложения **вывода** окне могут отображаться сведения о:  
  
-   Загруженные или выгруженные модули отладчика.  
  
-   Вызванные исключения.  
  
-   Завершившиеся процессы.  
  
-   Завершившиеся потоки.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Окно вывода](../ide/reference/output-window.md)   
 [Трассировка и инструментирование приложений](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
