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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842804"
---
# <a name="deleting-a-breakpoint"></a>Удаление точки останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс удаления ожидающей точки останова.  
  
## <a name="deletion-process"></a>Процесс удаления  
 Диспетчер отладки сеансов (SDM) вызывает метод [IDebugPendingBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) для удаления ожидающей точки останова и всех привязанных к ним точек останова.  
  
> [!NOTE]
> Можно также удалить одну привязанную точку останова с помощью вызова [IDebugBoundBreakpoint2::D удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
