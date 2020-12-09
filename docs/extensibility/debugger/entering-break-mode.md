---
title: Вход в режим приостановки | Документация Майкрософт
description: Сведения о процессе, который выполняется для точки останова, обнаруженной в функции, выполнении до строки исходного кода в курсоре или выполнении до точки останова.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e73c64d17aee48cdb67a110e93aa556f112a1014
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915236"
---
# <a name="enter-break-mode"></a>Переход в режим приостановки выполнения
Следующая информация описывает процесс, возникающий при обнаружении точки останова после пошаговой обработки в функции, выполнения до строки исходного кода, в которой находится курсор, или при выполнении в точке останова.

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

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
