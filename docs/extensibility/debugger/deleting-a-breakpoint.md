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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862179"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
Ниже описан процесс удаления ожидающей точки останова.

## <a name="deletion-process"></a>Процесс удаления
 Диспетчер отладки сеансов (SDM) вызывает метод [IDebugPendingBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) для удаления ожидающей точки останова и всех привязанных к ним точек останова.

> [!NOTE]
> Можно также удалить одну привязанную точку останова с помощью вызова [IDebugBoundBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
