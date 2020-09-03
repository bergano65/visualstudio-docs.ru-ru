---
title: Достижение точки останова | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738565"
---
# <a name="hit-a-breakpoint"></a>Попадание в точку останова
В следующем разделе описывается процесс, когда модуль отладки (DE) достигает точки останова при выполнении или пошаговом выполнении.

## <a name="troubleshoot-a-hit-breakpoint"></a>Устранение неполадок в точке останова

1. Параметр DE отправляет интерфейс [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) в качестве **EVENT_SYNC_STOP**.

2. Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2::: енумбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) для получения точки останова, которая была достигнута.

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
