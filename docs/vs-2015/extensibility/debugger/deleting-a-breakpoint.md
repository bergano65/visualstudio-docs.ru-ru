---
title: Удаление точки останова | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409410"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, при удалении ожидающая точка останова:  
  
## <a name="deletion-process"></a>Процесс удаления  
 Диспетчер отладки сеансов (SDM) вызывает [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) привязан метод для удаления ожидающая точка останова и всех связанных точек останова из него.  
  
> [!NOTE]
> Связанная точка останова также можно удалить с помощью вызова [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
