---
title: Удаление точки останова | Документация Майкрософт
description: Узнайте, как диспетчер отладки сеансов удаляет отложенную точку останова и все привязанные точки останова, привязанные к ней при удалении ожидающей точки останова.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915561"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
Ниже описан процесс удаления ожидающей точки останова.

## <a name="deletion-process"></a>Процесс удаления
 Диспетчер отладки сеансов (SDM) вызывает метод [IDebugPendingBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) для удаления ожидающей точки останова и всех привязанных к ним точек останова.

> [!NOTE]
> Можно также удалить одну привязанную точку останова с помощью вызова [IDebugBoundBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
