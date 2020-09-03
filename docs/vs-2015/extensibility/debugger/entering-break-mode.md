---
title: Вход в режим приостановки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182252"
---
# <a name="entering-break-mode"></a>Вход в режим приостановки выполнения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, который происходит при обнаружении точки останова после пошагового выполнения функции, выполняется до строки исходного кода, в которой находится курсор, или выполняется в точку останова.  
  
## <a name="break-mode-process"></a>Процесс режима приостановки выполнения  
  
1. Модуль отладки (DE) отправляет [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)или любое другое событие остановки, чтобы среда IDE переводила в режим приостановки.  
  
2. Модель SDM получает сведения о стеке вызовов из потока следующим образом:  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - [IDebugStackFrame2:: жетдокументконтекст](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) , чтобы получить сведения о исходном коде  
  
    - [IDebugDocumentContext2:: Name](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) для получения имени файла  
  
    - [IDebugDocumentContext2:: жетстатементранже](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) для получения диапазона инструкций  
  
    - [IDebugStackFrame2:: жеткодеконтекст](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) , чтобы получить сведения о памяти  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
