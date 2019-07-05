---
title: Диагностические сообщения в окне вывода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695300"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Диагностические сообщения в окне вывода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Во время выполнения сообщения в окне вывода можно написать с помощью класса Debug или Trace; оба класса входят в библиотеку классов <xref:System.Diagnostics>. Класс Debug используется, если необходимо выводить сообщение только в отладочной версии программы. Класс Trace используется в том случае, если необходимо выводить сообщение и в отладочной версии программы, и в выпускаемой.  
  
## <a name="output-methods"></a>Методы вывода  
 Классы <xref:System.Diagnostics.Trace> и <xref:System.Diagnostics.Debug> предоставляют следующие методы вывода:  
  
- Различные методы `Write`, которые выводят сведения без прерывания выполнения программы. Эти методы заменяют метод `Debug.Print`, который использовался в предыдущих версиях Visual Basic.  
  
- Методы <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, которые прерывают выполнение программы и выводят сведения, если заданное условие не выполняется. По умолчанию метод `Assert` отображает сведения в диалоговом окне. Дополнительные сведения см. в разделе [Утверждения в управляемом коде](../debugger/assertions-in-managed-code.md).  
  
- Методы <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, которые всегда прерывают выполнение программы и выводят сведения. По умолчанию методы `Fail` отображают сведения в диалоговом окне.  
  
  В дополнение к программному выводу приложения **вывода** окне могут отображаться сведения о:  
  
- Загруженные или выгруженные модули отладчика.  
  
- Вызванные исключения.  
  
- Завершившиеся процессы.  
  
- Завершившиеся потоки.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Окно вывода](../ide/reference/output-window.md)   
 [Трассировка и инструментирование приложений](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Введение к инструментированию и трассировка](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
