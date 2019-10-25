---
title: Как выполнить отладку метода OnStart | Документация Майкрософт
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
ms.openlocfilehash: 107ce6d5ca2b327d77fe588e1ac7ffda10a0a3a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733629"
---
# <a name="how-to-debug-the-onstart-method"></a>Практическое руководство. Отладка метода OnStart
Службу Windows можно отлаживать, запустив ее и подключив отладчик к процессу службы. Дополнительные сведения см. в [руководстве по отладке приложений-служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Тем не менее, для отладки метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> службы Windows необходимо запустить отладчик внутри метода.

1. Добавьте вызов <xref:System.Diagnostics.Debugger.Launch%2A> в начале метода `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Запустите службу (можно использовать `net start`или запустить ее в окне **Службы** ).

    Должно появиться диалоговое окно такого вида.

    ![онстартдебуг](../debugger/media/onstartdebug.png "онстартдебуг")

3. Выберите **Да, отладить \<имя_службы>.**

4. В окне отладчика JIT выберите версию Visual Studio, которую необходимо использовать для отладки.

    ![жустинтимедебугжер](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Запустится новый экземпляр Visual Studio, а выполнение будет остановлено на методе `Debugger.Launch()` .

## <a name="see-also"></a>См. также
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Отладка управляемого кода](../debugger/debugging-managed-code.md)
