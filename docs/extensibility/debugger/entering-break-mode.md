---
title: Режим ввода разбивки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738875"
---
# <a name="enter-break-mode"></a>Введите режим перерыва
Следующая информация описывает процесс, возникающий при возникновении точки разрыва после вступления в функцию, бегущей к строке исходного кода с курсорами в ней или бегущей к точке разрыва.

## <a name="break-mode-process"></a>Процесс работы режима разрыва

1. Отладка двигателя (DE) отправляет [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), или любое другое событие остановки, чтобы вызвать IDE ввести режим перерыва.

2. SDM получает информацию о стеке вызова из потока следующим образом:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext,](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) чтобы получить информацию об исходном коде

    - [IDebugDocumentContext2:GetName,](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) чтобы получить имя файла

    - [IDebugDocumentContext2::GetStatementRange,](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) чтобы получить диапазон оператора

    - [IDebugStackFrame2:GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) для получения информации о памяти

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
