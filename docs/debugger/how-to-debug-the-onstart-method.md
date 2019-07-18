---
title: Практическое руководство. Отладка метода OnStart | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fc5e8a7e0bbc80fd7fa0aa2d242239a9be6a219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894421"
---
# <a name="how-to-debug-the-onstart-method"></a>Практическое руководство. отладку метода OnStart
Службу Windows можно отлаживать, запустив ее и подключив отладчик к процессу службы. Дополнительные сведения см. в разделе [Как Отладка приложений служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Тем не менее, для отладки метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> службы Windows необходимо запустить отладчик внутри метода.

1. Добавьте вызов <xref:System.Diagnostics.Debugger.Launch%2A> в начале метода `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Запустите службу (можно использовать `net start`или запустить ее в окне **Службы** ).

    Должно появиться диалоговое окно такого вида.

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Выберите **Да, отладить \<имя_службы>.**

4. В окне отладчика JIT выберите версию Visual Studio, которую необходимо использовать для отладки.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Запустится новый экземпляр Visual Studio, а выполнение будет остановлено на методе `Debugger.Launch()` .

## <a name="see-also"></a>См. также
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
