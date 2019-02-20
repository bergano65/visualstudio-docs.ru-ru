---
title: 'Практическое: отладка метода OnStart | Документация Майкрософт'
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
ms.openlocfilehash: 2cfd6153389bbfe9cbbd36f33f6a2e4384509297
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227065"
---
# <a name="how-to-debug-the-onstart-method"></a>Практическое руководство. Отладка метода OnStart
Службу Windows можно отлаживать, запустив ее и подключив отладчик к процессу службы. Дополнительные сведения см. в разделе [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Тем не менее, для отладки метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> службы Windows необходимо запустить отладчик внутри метода.

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

## <a name="see-also"></a>См. также раздел
[Безопасность отладчика](../debugger/debugger-security.md)  
[Отладка управляемого кода](../debugger/debugging-managed-code.md)
