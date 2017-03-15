---
title: "Вход в режим приостановки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "режим приостановки"
  - "отладка [пакет SDK для отладки], вход в режим приостановки"
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Вход в режим приостановки
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс, возникающий при обнаружении точки останова после зайдя в функцию, выполняется к линии исходного кода, содержащий курсор в нем или выполнение в точке останова.  
  
## Процесс в режиме приостановки выполнения  
  
1.  Отладчик \(DE\) отправляет [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)"  [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)при остановке или любое другое событие для интегрированной среды разработки войти в режим приостановки выполнения.  
  
2.  SDM возвращает данные о стеке вызова из потока, следующим образом:  
  
    -   [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2:: GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)  
  
    -   [IEnumDebugFrameInfo2:: Далее](../Topic/IEnumDebugFrameInfo2::Next.md)  
  
    -   [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) получить данные из исходного кода  
  
    -   [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) получить имя файла  
  
    -   [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) получить диапазон выписки  
  
    -   [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) получить данные об использовании памяти  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)