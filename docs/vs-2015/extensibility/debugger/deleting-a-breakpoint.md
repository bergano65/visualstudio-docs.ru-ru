---
title: Удаление точки останова | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b20ac5b76dfcd24e0dbed5fbc08720c33d88fdd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254089"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, при удалении ожидающая точка останова:  
  
## <a name="deletion-process"></a>Процесс удаления  
 Диспетчер отладки сеансов (SDM) вызывает [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) привязан метод для удаления ожидающая точка останова и всех связанных точек останова из него.  
  
> [!NOTE]
>  Связанная точка останова также можно удалить с помощью вызова [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)

