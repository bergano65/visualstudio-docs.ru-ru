---
title: Исключение при обработке (SDK для Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 646479184061b093d5d84f81827a4106bd3cda47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="exception-handling-visual-studio-sdk"></a>Исключение при обработке (SDK для Visual Studio)
Далее описывается процесс, который происходит при возникновении исключения.  
  
## <a name="exception-handling-process"></a>Процесс обработки исключений  
  
1.  Если возникает исключение, но прежде чем он обрабатывается обработчиком исключений в отлаживаемой программы, отладчик (DE) отправляет [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) диспетчеру сеанса отладки (SDM) как событие остановки. `IDebugExceptionEvent2` Отправляется, если только параметры для исключения (указанный в диалоговом окне исключения отладочный пакет) укажите пользователь хочет остановить на уведомления о первом этапе обработки исключений.  
  
2.  Вызовы SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) для получения свойства исключения.  
  
3.  Вызовы отладки пакета [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) для определения, какие параметры предлагать пользователю.  
  
4.  Отладочный пакет запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения первого шанса.  
  
5.  Если пользователь решит продолжить, SDM вызывает [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Если метод возвращает значение S_OK, вызывает [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         - или -  
  
         Если метод возвращает значение S_FALSE, программа отлаживаемый получает вторая возможность обработки исключения.  
  
6.  Если отлаживаемая программа не имеет обработчика исключений вторичных, отправляет DE `IDebugExceptionEvent2` для SDM как **EVENT_SYNC_STOP**.  
  
7.  Отладочный пакет запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения первого шанса.  
  
8.  Вызовы отладки пакета [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) для определения, какие параметры предлагать пользователю.  
  
9. Отладочный пакет запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения вторичных.  
  
10. Если метод возвращает значение S_OK, вызывает `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)