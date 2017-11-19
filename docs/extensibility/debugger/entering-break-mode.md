---
title: "Вход в режим приостановки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33dd97cf627ae10e71a2aa2213a9763e86818b70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="entering-break-mode"></a>Вход в режим приостановки
Далее описывается процесс, который возникает при обнаружении точки останова после шаг с заходом в функцию, выполняется к строке исходного кода, содержащую курсор или до точки останова.  
  
## <a name="break-mode-process"></a>Процесс режима приостановки выполнения  
  
1.  Модуль отладки (DE) отправляет [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), или любое другое событие остановки, чтобы среда IDE перейти в режим приостановки выполнения.  
  
2.  SDM возвращает стек вызовов в потоке, следующим образом:  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) для получения сведений об исходном коде  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) удалось получить имя файла  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) получить диапазон инструкции  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) для получения сведений о памяти  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)