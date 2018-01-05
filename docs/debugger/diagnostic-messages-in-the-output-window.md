---
title: "Отправить диагностические сообщения в окне вывода | Документы Microsoft"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df071834a6ae36da0156c527284f6ffbfcee0e4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Отправить диагностические сообщения в окне вывода
Можно написать сообщения во время выполнения для **вывода** окна с помощью `Debug` класса или `Trace` класса, которые входят в состав из <xref:System.Diagnostics> библиотеки классов. Класс Debug используется, если необходимо выводить сообщение только в отладочной версии программы. Класс Trace используется в том случае, если необходимо выводить сообщение и в отладочной версии программы, и в выпускаемой.  
  
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