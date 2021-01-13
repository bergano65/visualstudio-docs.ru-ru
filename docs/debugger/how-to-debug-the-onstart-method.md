---
title: Отладка метода OnStart | Документация Майкрософт
description: Узнайте, как выполнить отладку метода OnStart службы Windows в Visual Studio, запустив отладчик из самого метода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 488fe471552256e8fad62bb6f831448811ca343f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903146"
---
# <a name="how-to-debug-the-onstart-method"></a>Практическое руководство. отладку метода OnStart
Службу Windows можно отлаживать, запустив ее и подключив отладчик к процессу службы. Дополнительные сведения см. в разделе [Практическое руководство. Отладка приложений служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Тем не менее, для отладки метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> службы Windows необходимо запустить отладчик внутри метода.

1. Добавьте вызов <xref:System.Diagnostics.Debugger.Launch%2A> в начале метода `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Запустите службу (можно использовать `net start`или запустить ее в окне **Службы** ).

    Должно появиться диалоговое окно такого вида.

    ![Снимок экрана: диалоговое окно JIT-отладчика Visual Studio, отображающее необработанное исключение .NET Framework, возникшее в WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Выберите **Да, запустить отладку \<service name>.**

4. В окне отладчика JIT выберите версию Visual Studio, которую необходимо использовать для отладки.

    ![Снимок экрана: окно JIT-отладчика Visual Studio с параметром "Новый экземпляр Microsoft Visual Studio 2015", выбранным со списка возможных отладчиков.](../debugger/media/justintimedebugger.png)

5. Запустится новый экземпляр Visual Studio, а выполнение будет остановлено на методе `Debugger.Launch()` .

## <a name="see-also"></a>См. также
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
