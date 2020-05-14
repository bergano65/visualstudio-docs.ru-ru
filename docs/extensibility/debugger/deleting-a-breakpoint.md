---
title: Удаляем точку разрыва (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738950"
---
# <a name="deleting-a-breakpoint"></a>Удаляние точки разрыва
Ниже описывается процесс при удалении отложенной точки разрыва:

## <a name="deletion-process"></a>Процесс удаления
 Менеджер отладки сеанса (SDM) вызывает [метод IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) для удаления ожидающего разрыва и всех связанных с ней точек разрыва.

> [!NOTE]
> Один связанный пункт разрыва также может быть удален путем вызова [на IDebugBoundBreakpoint2::Delete.](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)

## <a name="see-also"></a>См. также
- [События отладки вызова](../../extensibility/debugger/calling-debugger-events.md)
