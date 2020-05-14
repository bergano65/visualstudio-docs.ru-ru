---
title: Ошибки точки разрыва (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739214"
---
# <a name="breakpoint-errors"></a>Ошибки точки разрыва
Ниже описывается процесс, когда точка разрыва пытается привязаться к коду, но не удается.

## <a name="troubleshoot-a-breakpoint-error"></a>Устранение проблемы ошибки точки разрыва

1. Отладка двигателя (DE) отправляет [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) в сеанс отладки менеджера (SDM).

2. SDM вызывает [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2) `ppErrorBP`для получения точки разрыва ошибки.

3. SDM вызывает [IDebugErrorBreakpoint2::GetPendingBreakpoint,](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) чтобы получить отложенную точку разрыва, из которой возникла точка разрыва ошибки.

4. SDM вызывает [IDebugErrorBreakpoint2::GetBreakpointResolution,](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) чтобы получить причину, по которой точка разрыва ошибки не удалось связать.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
