---
title: Практическое руководство. Отладка метода OnStart | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 391b906889dcbe422f7ec227b1d375be82e7ac91
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700176"
---
# <a name="how-to-debug-the-onstart-method"></a>Практическое руководство. отладку метода OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Службу Windows можно отлаживать, запустив ее и подключив отладчик к процессу службы. Дополнительные сведения см. в разделе [Практическое руководство. Отладка приложений служб Windows](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). Тем не менее, для отладки метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> службы Windows необходимо запустить отладчик внутри метода.  
  
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
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
