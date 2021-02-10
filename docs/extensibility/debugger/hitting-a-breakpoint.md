---
title: Достижение точки останова | Документация Майкрософт
description: В этой статье описывается процесс, который происходит при попадании отладчика в точку останова во время работы или пошагового выполнения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 808bf95631bb4106d071c29d7af233d071ef5229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947727"
---
# <a name="hit-a-breakpoint"></a>Попадание в точку останова
В следующем разделе описывается процесс, когда модуль отладки (DE) достигает точки останова при выполнении или пошаговом выполнении.

## <a name="troubleshoot-a-hit-breakpoint"></a>Устранение неполадок в точке останова

1. Параметр DE отправляет интерфейс [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) в качестве **EVENT_SYNC_STOP**.

2. Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2::: енумбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) для получения точки останова, которая была достигнута.

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
