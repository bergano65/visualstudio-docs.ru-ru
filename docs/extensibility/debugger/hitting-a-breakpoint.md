---
title: Нажатие точки разрыва (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738565"
---
# <a name="hit-a-breakpoint"></a>Попадание в точку останова
В следующем разделе описывается процесс, когда движок отладки (DE) попадает в точку разрыва во время выполнения или шага:

## <a name="troubleshoot-a-hit-breakpoint"></a>Устранение неполадок точки разрыва удара

1. DE отправляет интерфейс [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) в качестве **EVENT_SYNC_STOP.**

2. Менеджер отладки сеанса (SDM) вызывает [IDebugBreakpointEvent2:::EnumBreakpoints,](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) чтобы получить точку разрыва, которая была поражена.

## <a name="see-also"></a>См. также
- [События отладки вызова](../../extensibility/debugger/calling-debugger-events.md)
