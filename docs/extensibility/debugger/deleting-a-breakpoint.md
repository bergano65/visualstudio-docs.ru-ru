---
title: Удаление точки останова | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738950"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
Ниже описан процесс удаления ожидающей точки останова.

## <a name="deletion-process"></a>Процесс удаления
 Диспетчер отладки сеансов (SDM) вызывает метод [IDebugPendingBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) для удаления ожидающей точки останова и всех привязанных к ним точек останова.

> [!NOTE]
> Можно также удалить одну привязанную точку останова с помощью вызова [IDebugBoundBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>См. также
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
