---
title: Удаление точки останова | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bff63c243590db91ea97055943b89d73ea00308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104434"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
Далее описывается процесс, при удалении ожидающая точка останова:  
  
## <a name="deletion-process"></a>Процесс удаления  
 Диспетчер сеансов отладки (SDM) вызывает [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) привязан метод для удаления ожидающая точка останова и всех связанных точек останова из него.  
  
> [!NOTE]
>  Связанная точка останова, также будут удалены с помощью вызова [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)