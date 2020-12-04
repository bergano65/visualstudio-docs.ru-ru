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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560854"
---
# <a name="hit-a-breakpoint"></a>Попадание в точку останова
В следующем разделе описывается процесс, когда модуль отладки (DE) достигает точки останова при выполнении или пошаговом выполнении.

## <a name="troubleshoot-a-hit-breakpoint"></a>Устранение неполадок в точке останова

1. Параметр DE отправляет интерфейс [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) в качестве **EVENT_SYNC_STOP**.

2. Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2::: енумбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) для получения точки останова, которая была достигнута.

## <a name="see-also"></a>См. также
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
